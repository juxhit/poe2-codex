# Skill Builder Calculator

> Interactive prototype: pick a base skill, socket supports and a meta gem, see tag compatibility, cost and damage multipliers, and warnings.
> **Data disclaimer:** values are representative approximations from the 0.5.x catalog ([skill-gems.md](skill-gems.md), [support-gems.md](support-gems.md)) — always verify exact numbers in-game or on [poe2db](https://poe2db.tw/us/Skill_Gems). Not affiliated with GGG.

<div id="calc" style="border:1px solid var(--md-default-fg-color--lightest); border-radius:8px; padding:1em; background:var(--md-default-bg-color--light);">

### 1 · Base skill

<select id="skill" style="width:100%; padding:8px; font-size:14px;"></select>
<div id="skillinfo" style="margin-top:6px; font-size:13px; opacity:.85;"></div>

### 2 · Support sockets

Socket count:
<select id="sockets" style="padding:6px;">
  <option value="3">3 (Lesser Jeweller's Orb)</option>
  <option value="4" selected>4 (Greater)</option>
  <option value="5">5 (Perfect)</option>
</select>

### 3 · Support gems

<div id="supports" style="display:flex; flex-direction:column; gap:6px; margin:8px 0;"></div>
<button id="addsup" style="padding:6px 14px; cursor:pointer;">+ Add support gem</button>

### 4 · Meta gem (optional)

<select id="meta" style="width:100%; padding:8px; font-size:14px;"></select>

### Result

<div id="result" style="line-height:1.6;"></div>

</div>

<script>
const SKILLS = {
  "Spark": {lvl:1, tags:["Spell","Projectile","Lightning","Duration","Chaining"], weapon:"Any", cost:1, family:"Elemental"},
  "Ice Nova": {lvl:1, tags:["Spell","AoE","Cold","Nova"], weapon:"Any", cost:1, family:"Elemental"},
  "Fireball": {lvl:3, tags:["Spell","AoE","Projectile","Fire"], weapon:"Any", cost:1, family:"Elemental"},
  "Comet": {lvl:11, tags:["Spell","AoE","Cold"], weapon:"Any", cost:1, family:"Elemental"},
  "Lightning Conduit": {lvl:13, tags:["Spell","AoE","Lightning"], weapon:"Any", cost:1, family:"Elemental"},
  "Boneshatter": {lvl:1, tags:["Attack","AoE","Melee","Strike","Physical"], weapon:"Mace", cost:1, family:"Mace"},
  "Volcanic Fissure": {lvl:7, tags:["Attack","AoE","Melee","Slam","Fire","Duration"], weapon:"Mace", cost:1, family:"Mace"},
  "Ice Strike": {lvl:5, tags:["Attack","AoE","Melee","Strike","Cold"], weapon:"Quarterstaff", cost:1, family:"Staff"},
  "Tempest Flurry": {lvl:5, tags:["Attack","AoE","Melee","Strike","Lightning"], weapon:"Quarterstaff", cost:1, family:"Staff"},
  "Lightning Arrow": {lvl:1, tags:["Attack","AoE","Projectile","Lightning","Chaining"], weapon:"Bow", cost:1, family:"Bow"},
  "Ice Shot": {lvl:9, tags:["Attack","Projectile","Cold","Repeatable"], weapon:"Bow", cost:1, family:"Bow"},
  "Lightning Spear": {lvl:3, tags:["Attack","AoE","Projectile","Lightning","Repeatable"], weapon:"Spear", cost:1, family:"Spear"},
  "Explosive Shot": {lvl:7, tags:["Attack","AoE","Ammunition","Projectile","Fire","Detonator"], weapon:"Crossbow", cost:1, family:"Crossbow"},
  "Galvanic Shards": {lvl:5, tags:["Attack","Ammunition","Projectile","Lightning","Chaining","Merging"], weapon:"Crossbow", cost:1, family:"Crossbow"},
  "Contagion": {lvl:1, tags:["Spell","AoE","Chaos","Duration"], weapon:"Any", cost:1, family:"Occult"},
  "Essence Drain": {lvl:3, tags:["Spell","Projectile","Chaos","Duration"], weapon:"Any", cost:1, family:"Occult"},
  "Furious Slam": {lvl:1, tags:["Attack","Shapeshift","AoE","Melee","Slam"], weapon:"Talisman", cost:1, family:"Primal"},
};
const SUPPORTS = {
  // name: [tier, cost mult (more), effect summary, required tags, more-damage mult or null]
  "Arcane Surge": [1, 1.0, "Grants Arcane Surge after spending enough mana (cast speed + mana regen)", ["Spell"], null],
  "Controlled Destruction": [1, 1.0, "+25% spell damage, cannot crit", ["Spell"], {inc:25}],
  "Scattered Damage / Multishot I": [1, 1.15, "+2 projectiles, less damage", ["Projectile"], {more:-20}],
  "Chain I": [1, 1.1, "+1 chain, less damage", ["Projectile","Chaining"], {more:-15}],
  "Fork": [3, 1.1, "Projectiles fork", ["Projectile"], null],
  "Pierce I": [1, 1.0, "Projectiles pierce 1 enemy", ["Projectile"], null],
  "Heft": [5, 1.2, "+30% max physical hit damage", ["Physical"], null],
  "Brutality I": [1, 1.15, "More phys damage, no elemental/chaos", ["Physical"], {more:20}],
  "Fire Attunement": [1, 1.0, "25% of damage converted to Fire, −50% other types", [], null],
  "Cold Attunement": [1, 1.0, "25% of damage converted to Cold, −50% other types", [], null],
  "Lightning Attunement": [1, 1.0, "25% of damage converted to Lightning, −50% other types", [], null],
  "Ignite I": [1, 1.05, "Attacks/spells can Ignite", [], null],
  "Shock": [1, 1.0, "+100% chance to Shock", [], null],
  "Primal Armament": [1, 1.1, "More elemental attack damage", ["Attack"], {more:15}],
  "Momentum": [2, 1.0, "More damage after moving during use", [], {more:15}],
  "Executive Finesse": [1, 1.0, "Faster attacks with less damage (speed/qol)", ["Attack"], {more:-10}],
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

const skillSel = document.getElementById('skill');
const metaSel = document.getElementById('meta');
const supBox = document.getElementById('supports');
const socketsSel = document.getElementById('sockets');
Object.keys(SKILLS).forEach(k => skillSel.add(new Option(`${k} (${SKILLS[k].family}, lvl ${SKILLS[k].lvl})`, k)));
Object.keys(METAS).forEach(k => metaSel.add(new Option(k, k)));

function addSupportRow() {
  const row = document.createElement('div');
  row.style.display = 'flex'; row.style.gap = '6px'; row.style.alignItems = 'center';
  const sel = document.createElement('select');
  sel.style.flex = '1'; sel.style.padding = '6px';
  sel.add(new Option('— choose support —', ''));
  Object.keys(SUPPORTS).forEach(k => sel.add(new Option(`[${SUPPORTS[k][0]}★] ${k}`, k)));
  sel.onchange = render;
  const del = document.createElement('button');
  del.textContent = '✕'; del.style.padding = '4px 10px'; del.style.cursor = 'pointer';
  del.onclick = () => { row.remove(); render(); };
  row.append(sel, del);
  supBox.appendChild(row);
  sel.onchange();
}
document.getElementById('addsup').onclick = addSupportRow;

function render() {
  const skill = SKILLS[skillSel.value];
  const socketMax = +socketsSel.value;
  const picks = [...supBox.querySelectorAll('select')].map(s => s.value).filter(v => v);
  const meta = METAS[metaSel.value];
  const out = [];

  // socket limit
  if (picks.length > socketMax) out.push(`🚫 <b>${picks.length} supports socketed but gem has only ${socketMax} sockets</b> — use a higher Jeweller's Orb or remove one.`);

  // duplicates
  const dup = picks.filter((v, i) => picks.indexOf(v) !== i);
  if (dup.length) out.push(`⚠️ <b>Duplicate supports:</b> ${[...new Set(dup)].join(', ')} — each support may appear only once per skill.`);

  // tag compatibility
  const incompatible = picks.filter(name => {
    const req = SUPPORTS[name][3];
    return req.length && !req.some(t => skill.tags.includes(t));
  });
  incompatible.forEach(name => out.push(`🚫 <b>${name}</b> requires one of [${SUPPORTS[name][3].join(', ')}] — <b>${skillSel.value}</b> has [${skill.tags.join(', ')}]. Won't work.`));

  // numbers
  let cost = 1, more = 0, moreList = [], effects = [];
  picks.filter(name => !incompatible.includes(name)).forEach(name => {
    const [, cm, eff, , md] = SUPPORTS[name];
    cost *= cm;
    if (md) { more += md.more || 0; moreList.push(`${name}: ${md.more > 0 ? '+' : ''}${md.more}%`); }
    effects.push(`• <b>${name}</b> — ${eff}`);
  });

  out.push(`<hr style="opacity:.3">`);
  out.push(`<b>Skill:</b> ${skillSel.value} — lvl ${skill.lvl}, ${skill.family}, weapon: ${skill.weapon}`);
  out.push(`<b>Tags:</b> ${skill.tags.join(' · ')}`);
  out.push(`<b>Support sockets:</b> ${picks.length}/${socketMax}`);
  if (picks.length) {
    out.push(`<b>Mana/Energy cost multiplier:</b> ×${cost.toFixed(2)} ${cost > 1.3 ? '🔥 expensive — plan mana regen' : ''}`);
    if (more !== 0) out.push(`<b>Net damage from supports:</b> ${more > 0 ? '+' : ''}${more}% (sum of: ${moreList.join(', ')})`);
    out.push(`<b>Effects:</b><br>${effects.join('<br>')}`);
  }
  if (metaSel.value !== 'None') {
    out.push(`<hr style="opacity:.3">`);
    out.push(`<b>Meta:</b> ${metaSel.value}`);
    if (meta.energy) out.push(`⚡ ${meta.energy}`);
    if (meta.note) out.push(`💡 ${meta.note}`);
    out.push(`Meta gems accumulate <a href="meta-gems.md">Energy</a> from their trigger; at max Energy all socketed spells fire automatically. Scale Energy by pairing a fast trigger with slow, expensive spells.`);
  }

  out.push(`<hr style="opacity:.3"><span style="font-size:12px;opacity:.7">Prototype v0.1 · representative values · see <a href="skill-gems.md">skill catalog</a> · <a href="support-gems.md">support catalog</a> · <a href="meta-gems.md">meta gems</a></span>`);
  document.getElementById('result').innerHTML = out.join('<br>');
}
skillSel.onchange = render;
metaSel.onchange = render;
socketsSel.onchange = render;
addSupportRow();
render();
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
