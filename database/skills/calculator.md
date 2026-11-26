# Skill Builder Calculator

> Interactive prototype: pick a base skill, socket supports and a meta gem, see tag compatibility, cost and damage multipliers, and warnings.
> **Data disclaimer:** values are representative approximations from the 0.5.x catalog ([skill-gems.md](skill-gems.md), [support-gems.md](support-gems.md)) — always verify exact numbers in-game or on [poe2db](https://poe2db.tw/us/Skill_Gems).

<div class="calc" id="calc">

<div>
<h3>1 · Base skill</h3>
<select id="skill"></select>
<div id="skillinfo" style="margin-top:6px; font-size:12px; opacity:.8;"></div>
</div>

<div>
<h3>4 · Meta gem (optional)</h3>
<select id="meta"></select>
</div>

<div>
<h3>2 · Support sockets</h3>
<select id="sockets">
  <option value="3">3 — Lesser Jeweller's Orb</option>
  <option value="4" selected>4 — Greater</option>
  <option value="5">5 — Perfect</option>
</select>
</div>

<div class="calc-full">
<h3>3 · Support gems</h3>
<div id="supports" style="display:flex; flex-direction:column; gap:6px;"></div>
<p><button id="addsup">+ Add support gem</button></p>
</div>

<div class="result" id="result"></div>

</div>

<script>
const UI = {
  choose: "— choose support —",
  skill: s => `${s.name} (${s.family}, lvl ${s.lvl})`,
  sockets: n => `${n} sockets`,
  overflow: (n, m) => `🚫 <b>${n} supports socketed but the gem has only ${m} sockets</b> — use a higher Jeweller's Orb or remove one.`,
  dup: d => `⚠️ <b>Duplicate supports:</b> ${[...new Set(d)].join(", ")} — each support may appear only once per skill.`,
  incompat: (name, req, tags) => `🚫 <b>${name}</b> requires one of [${req.join(", ")}] — this skill has [${tags.join(", ")}]. Won't work.`,
  skillLine: (v, s) => `<b>Skill:</b> ${v} — lvl ${s.lvl}, ${s.family}, weapon: ${s.weapon}`,
  tags: t => `<b>Tags:</b> ${t.join(" · ")}`,
  socketsLine: (p, m) => `<b>Support sockets:</b> ${p}/${m}`,
  cost: (c, warn) => `<b>Cost multiplier:</b> ×${c.toFixed(2)} ${warn ? "🔥 expensive — plan mana regen" : ""}`,
  dmg: (m, l) => `<b>Net damage from supports:</b> ${m > 0 ? "+" : ""}${m}% (${l})`,
  metaLine: v => `<b>Meta:</b> ${v}`,
  footer: `Prototype v0.2 · representative values · see <a href="skill-gems.md">skill catalog</a> · <a href="support-gems.md">support catalog</a> · <a href="meta-gems.md">meta gems</a>`,
};
const SKILLS = {
  "Spark": {lvl:1, tags:["Spell","Projectile","Lightning","Duration","Chaining"], weapon:"Any", family:"Elemental"},
  "Ice Nova": {lvl:1, tags:["Spell","AoE","Cold","Nova"], weapon:"Any", family:"Elemental"},
  "Fireball": {lvl:3, tags:["Spell","AoE","Projectile","Fire"], weapon:"Any", family:"Elemental"},
  "Comet": {lvl:11, tags:["Spell","AoE","Cold"], weapon:"Any", family:"Elemental"},
  "Lightning Conduit": {lvl:13, tags:["Spell","AoE","Lightning"], weapon:"Any", family:"Elemental"},
  "Boneshatter": {lvl:1, tags:["Attack","AoE","Melee","Strike","Physical"], weapon:"Mace", family:"Mace"},
  "Volcanic Fissure": {lvl:7, tags:["Attack","AoE","Melee","Slam","Fire","Duration"], weapon:"Mace", family:"Mace"},
  "Ice Strike": {lvl:5, tags:["Attack","AoE","Melee","Strike","Cold"], weapon:"Quarterstaff", family:"Staff"},
  "Tempest Flurry": {lvl:5, tags:["Attack","AoE","Melee","Strike","Lightning"], weapon:"Quarterstaff", family:"Staff"},
  "Lightning Arrow": {lvl:1, tags:["Attack","AoE","Projectile","Lightning","Chaining"], weapon:"Bow", family:"Bow"},
  "Ice Shot": {lvl:9, tags:["Attack","Projectile","Cold","Repeatable"], weapon:"Bow", family:"Bow"},
  "Lightning Spear": {lvl:3, tags:["Attack","AoE","Projectile","Lightning","Repeatable"], weapon:"Spear", family:"Spear"},
  "Explosive Shot": {lvl:7, tags:["Attack","AoE","Ammunition","Projectile","Fire","Detonator"], weapon:"Crossbow", family:"Crossbow"},
  "Galvanic Shards": {lvl:5, tags:["Attack","Ammunition","Projectile","Lightning","Chaining","Merging"], weapon:"Crossbow", family:"Crossbow"},
  "Contagion": {lvl:1, tags:["Spell","AoE","Chaos","Duration"], weapon:"Any", family:"Occult"},
  "Essence Drain": {lvl:3, tags:["Spell","Projectile","Chaos","Duration"], weapon:"Any", family:"Occult"},
  "Furious Slam": {lvl:1, tags:["Attack","Shapeshift","AoE","Melee","Slam"], weapon:"Talisman", family:"Primal"},
};
const SUPPORTS = {
  "Arcane Surge": [1, 1.0, "Grants Arcane Surge after spending enough mana (cast speed + mana regen)", ["Spell"], null],
  "Controlled Destruction": [1, 1.0, "+25% spell damage, cannot crit", ["Spell"], {inc:25}],
  "Multishot I": [1, 1.15, "+2 projectiles, less damage", ["Projectile"], {more:-20}],
  "Chain I": [1, 1.1, "+1 chain, less damage", ["Projectile","Chaining"], {more:-15}],
  "Fork": [3, 1.1, "Projectiles fork", ["Projectile"], null],
  "Pierce I": [1, 1.0, "Projectiles pierce 1 enemy", ["Projectile"], null],
  "Heft": [5, 1.2, "+30% max physical hit damage", ["Physical"], null],
  "Brutality I": [1, 1.15, "More phys damage, no elemental/chaos", ["Physical"], {more:20}],
  "Fire Attunement": [1, 1.0, "25% of damage becomes Fire, −50% other types", [], null],
  "Cold Attunement": [1, 1.0, "25% of damage becomes Cold, −50% other types", [], null],
  "Lightning Attunement": [1, 1.0, "25% of damage becomes Lightning, −50% other types", [], null],
  "Ignite I": [1, 1.05, "Hits can Ignite", [], null],
  "Shock": [1, 1.0, "+100% chance to Shock", [], null],
  "Primal Armament": [1, 1.1, "More elemental attack damage", ["Attack"], {more:15}],
  "Momentum": [2, 1.0, "More damage after moving during use", [], {more:15}],
  "Unleash": [1, 1.3, "Seals: repeat the spell per Seal", ["Spell","Repeatable"], {more:-25}],
  "Spell Echo": [2, 1.4, "Spell repeats", ["Spell"], {more:-20}],
  "Magnified Area I": [1, 1.1, "Bigger AoE", ["AoE"], null],
  "Concentrated Area": [1, 1.0, "Smaller AoE, more damage", ["AoE"], {more:20}],
  "Cold Penetration": [2, 1.15, "30% Cold penetration (dead vs ≤0% res)", ["Cold"], null],
  "Lightning Penetration": [2, 1.15, "30% Lightning penetration", ["Lightning"], null],
  "Fire Penetration I": [2, 1.15, "Fire penetration", ["Fire"], null],
  "Elemental Focus": [3, 1.2, "More elemental damage, no ailments", ["Cold","Fire","Lightning"], {more:25}],
  "Deadly Poison I": [2, 1.1, "Chance to Poison, more poison damage", [], null],
  "Bleed I": [1, 1.05, "Chance to Bleed", ["Physical"], null],
  "Second Wind I": [2, 1.2, "+1 cooldown use", [], null],
  "Empowered Damage I": [1, 1.0, "Empowered skills deal more damage", [], {more:20}],
  "Life Drain": [1, 1.0, "Recover Life on Culling kills", [], null],
  "Minion Pact I": [1, 1.0, "Minions share buffs", ["Minion"], null],
  "Meat Shield I": [1, 1.0, "Minions taunt & tank", ["Minion"], null],
  "Feeding Frenzy I": [3, 1.1, "Minions Frenzy on kill", ["Minion"], null],
};
const METAS = {
  "None": {},
  "Cast on Critical (L14)": {energy:"1 Energy per Power of crit enemies (socketed skills −20% damage)", note:"Best with fast-crit skills + slow expensive spells"},
  "Cast on Elemental Ailment (L14)": {energy:"10/Power on Freeze, 1/Power on Shock & Ignite", note:"Pair with ailment-focused skills"},
  "Cast on Minion Death (L8)": {energy:"50 base Energy per persistent minion killed", note:"Suicide-minion loops"},
  "Cast on Dodge (L14)": {energy:"2 Energy per metre dodge-rolled", note:"Movement-driven builds"},
  "Mirage Archer (L8)": {note:"Dodge roll → Mirage fires socketed ranged attacks (30% less dmg)"},
  "Blasphemy (L8)": {note:"Curses become auras (60 Spirit each)"},
};

const $ = id => document.getElementById(id);
const skillSel = $("skill"), metaSel = $("meta"), supBox = $("supports"),
      socketsSel = $("sockets"), resultBox = $("result");
Object.keys(SKILLS).forEach(k => skillSel.add(new Option(UI.skill({name:k, ...SKILLS[k]}), k)));
Object.keys(METAS).forEach(k => metaSel.add(new Option(k, k)));

function render() {
  const skill = SKILLS[skillSel.value];
  const socketMax = +socketsSel.value;
  const picks = [...supBox.querySelectorAll("select")].map(s => s.value).filter(Boolean);
  const meta = METAS[metaSel.value];
  const out = [];

  if (picks.length > socketMax)
    out.push(UI.overflow(picks.length, socketMax));
  const dup = picks.filter((v, i) => picks.indexOf(v) !== i);
  if (dup.length) out.push(UI.dup(dup));
  const incompatible = picks.filter(n => {
    const req = SUPPORTS[n][3];
    return req.length && !req.some(t => skill.tags.includes(t));
  });
  incompatible.forEach(n => out.push(UI.incompat(n, SUPPORTS[n][3], skill.tags)));

  out.push("<hr>");
  out.push(UI.skillLine(skillSel.value, skill));
  out.push(UI.tags(skill.tags));
  out.push(UI.socketsLine(picks.length, socketMax));
  let cost = 1, more = 0, moreList = [], effects = [];
  picks.filter(n => !incompatible.includes(n)).forEach(n => {
    const [, cm, eff, , md] = SUPPORTS[n];
    cost *= cm;
    if (md) { more += md.more || 0; moreList.push(`${n}: ${md.more > 0 ? "+" : ""}${md.more}%`); }
    effects.push(`• <b>${n}</b> — ${eff}`);
  });
  if (picks.length) {
    out.push(UI.cost(cost, cost > 1.3));
    if (more !== 0) out.push(UI.dmg(more, moreList.join(", ")));
    out.push("<b>Effects:</b><br>" + effects.join("<br>"));
  }
  if (metaSel.value !== "None") {
    out.push("<hr>");
    out.push(UI.metaLine(metaSel.value));
    if (meta.energy) out.push("⚡ " + meta.energy);
    if (meta.note) out.push("💡 " + meta.note);
    out.push(`Meta gems accumulate <a href="meta-gems.md">Energy</a> from their trigger; at max Energy all socketed spells fire automatically.`);
  }
  out.push('<hr><span style="font-size:11px;opacity:.7">' + UI.footer + "</span>");
  resultBox.innerHTML = out.join("<br>");
}
function addSupportRow() {
  const row = document.createElement("div");
  row.className = "row";
  const sel = document.createElement("select");
  sel.add(new Option(UI.choose, ""));
  Object.keys(SUPPORTS).forEach(k => sel.add(new Option(`[${SUPPORTS[k][0]}★] ${k}`, k)));
  sel.onchange = render;
  const del = document.createElement("button");
  del.textContent = "✕";
  del.onclick = () => { row.remove(); render(); };
  row.append(sel, del);
  supBox.appendChild(row);
  render();
}
skillSel.onchange = render;
metaSel.onchange = render;
socketsSel.onchange = render;
$("addsup").onclick = addSupportRow;
addSupportRow();
</script>

## How this improves on a flat catalog

- **Tag compatibility is the #1 mistake** — the calculator blocks supports whose tags the skill lacks (e.g. Multishot on a non-projectile spell).
- **Socket budget** — shows when you've exceeded the 3/4/5 Jeweller's Orb limit.
- **Cost multiplier** — stacking expensive supports (Unleash ×1.3, Spell Echo ×1.4) is the classic mana-starvation trap.
- **Damage math** — supports grant *more* multipliers: they sum per-type here (the real game applies them multiplicatively — treat this as a rough comparison tool, not an exact DPS meter).

## Planned v2

- Full gem dataset auto-generated from poe2db (per-gem cost multipliers & exact %s)
- Support-duplicate rule toggle (EA launch rule vs current)
- Save/share builds via URL hash
- Meta Energy threshold calculator (cast-time based)

Related: [skill-gems.md](skill-gems.md) · [support-gems.md](support-gems.md) · [meta-gems.md](meta-gems.md) · [uncut-tiers.md](uncut-tiers.md)
