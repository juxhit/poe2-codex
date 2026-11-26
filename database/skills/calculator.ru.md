# Калькулятор скиллов

> Интерактивный прототип: выберите базовый скилл, вставьте камни поддержки и мета-камень — получите совместимость по тегам, множители стоимости и урона, предупреждения.
> **Дисклеймер по данным:** значения — репрезентативные приближения из каталога 0.5.x ([skill-gems.md](skill-gems.md), [support-gems.md](support-gems.md)) — точные числа проверяйте в игре или на [poe2db](https://poe2db.tw/us/Skill_Gems).

<div class="calc" id="calc">

<div>
<h3>1 · Базовый скилл</h3>
<select id="skill"></select>
<div id="skillinfo" style="margin-top:6px; font-size:12px; opacity:.8;"></div>
</div>

<div>
<h3>4 · Мета-камень (опционально)</h3>
<select id="meta"></select>
</div>

<div>
<h3>2 · Сокеты поддержки</h3>
<select id="sockets">
  <option value="3">3 — Lesser Jeweller's Orb</option>
  <option value="4" selected>4 — Greater</option>
  <option value="5">5 — Perfect</option>
</select>
</div>

<div class="calc-full">
<h3>3 · Камни поддержки</h3>
<div id="supports" style="display:flex; flex-direction:column; gap:6px;"></div>
<p><button id="addsup">+ Добавить камень поддержки</button></p>
</div>

<div class="result" id="result"></div>

</div>

<script>
const UI = {
  choose: "— выберите камень поддержки —",
  skill: s => `${s.name} (${s.family}, ур. ${s.lvl})`,
  overflow: (n, m) => `🚫 <b>Вставлено ${n} камней, а у гема только ${m} сокетов</b> — используйте Jeweller's Orb выше или уберите один.`,
  dup: d => `⚠️ <b>Дубликаты:</b> ${[...new Set(d)].join(", ")} — каждый саппорт может стоять в скилле только один раз.`,
  incompat: (name, req, tags) => `🚫 <b>${name}</b> требует один из тегов [${req.join(", ")}] — у скилла [${tags.join(", ")}]. Не сработает.`,
  skillLine: (v, s) => `<b>Скилл:</b> ${v} — ур. ${s.lvl}, ${s.family}, оружие: ${s.weapon}`,
  tags: t => `<b>Теги:</b> ${t.join(" · ")}`,
  socketsLine: (p, m) => `<b>Сокеты поддержки:</b> ${p}/${m}`,
  cost: (c, warn) => `<b>Множитель стоимости:</b> ×${c.toFixed(2)} ${warn ? "🔥 дорого — позаботьтесь о регене маны" : ""}`,
  dmg: (m, l) => `<b>Урон от саппортов:</b> ${m > 0 ? "+" : ""}${m}% (${l})`,
  metaLine: v => `<b>Мета-камень:</b> ${v}`,
  footer: `Прототип v0.2 · приблизительные значения · каталоги: <a href="skill-gems.md">скиллы</a> · <a href="support-gems.md">саппорты</a> · <a href="meta-gems.md">мета-камни</a>`,
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
  "Arcane Surge": [1, 1.0, "Д Arcane Surge после траты маны (скорость каста + реген маны)", ["Spell"], null],
  "Controlled Destruction": [1, 1.0, "+25% урона заклинаний, без критов", ["Spell"], {inc:25}],
  "Multishot I": [1, 1.15, "+2 снаряда, меньше урона", ["Projectile"], {more:-20}],
  "Chain I": [1, 1.1, "+1 цепь, меньше урона", ["Projectile","Chaining"], {more:-15}],
  "Fork": [3, 1.1, "Снаряды раздваиваются", ["Projectile"], null],
  "Pierce I": [1, 1.0, "Снаряды пробивают 1 врага", ["Projectile"], null],
  "Heft": [5, 1.2, "+30% макс. физического удара", ["Physical"], null],
  "Brutality I": [1, 1.15, "Больше физ. урона, без стихий/хаоса", ["Physical"], {more:20}],
  "Fire Attunement": [1, 1.0, "25% урона становится Огнём, −50% прочих типов", [], null],
  "Cold Attunement": [1, 1.0, "25% урона становится Холодом, −50% прочих типов", [], null],
  "Lightning Attunement": [1, 1.0, "25% урона становится Молнией, −50% прочих типов", [], null],
  "Ignite I": [1, 1.05, "Удары могут поджигать", [], null],
  "Shock": [1, 1.0, "+100% шанс шока", [], null],
  "Primal Armament": [1, 1.1, "Больше стихийного атакующего урона", ["Attack"], {more:15}],
  "Momentum": [2, 1.0, "Больше урона после движения во время использования", [], {more:15}],
  "Unleash": [1, 1.3, "Печати: повтор заклинания за каждую печать", ["Spell","Repeatable"], {more:-25}],
  "Spell Echo": [2, 1.4, "Заклинание повторяется", ["Spell"], {more:-20}],
  "Magnified Area I": [1, 1.1, "Больше область действия", ["AoE"], null],
  "Concentrated Area": [1, 1.0, "Меньше область, больше урона", ["AoE"], {more:20}],
  "Cold Penetration": [2, 1.15, "30% пробивания холода (бесполезно при ≤0% реза)", ["Cold"], null],
  "Lightning Penetration": [2, 1.15, "30% пробивания молнии", ["Lightning"], null],
  "Fire Penetration I": [2, 1.15, "Пробивание огня", ["Fire"], null],
  "Elemental Focus": [3, 1.2, "Больше стихийного урона, без статусных эффектов", ["Cold","Fire","Lightning"], {more:25}],
  "Deadly Poison I": [2, 1.1, "Шанс отравления, больше урона ядом", [], null],
  "Bleed I": [1, 1.05, "Шанс кровотечения", ["Physical"], null],
  "Second Wind I": [2, 1.2, "+1 использование кулдауна", [], null],
  "Empowered Damage I": [1, 1.0, "Усиленные умения наносят больше урона", [], {more:20}],
  "Life Drain": [1, 1.0, "Восстановление жизни при добиваниях", [], null],
  "Minion Pact I": [1, 1.0, "Миньоны делят баффы", ["Minion"], null],
  "Meat Shield I": [1, 1.0, "Миньоны провоцируют и танканут", ["Minion"], null],
  "Feeding Frenzy I": [3, 1.1, "Миньоны впадают в Frenzy при убийстве", ["Minion"], null],
};
const METAS = {
  "Нет": {},
  "Cast on Critical (ур.14)": {energy:"1 Energy за Power критующего врага (скиллы в сокетах −20% урона)", note:"Лучше с быстрыми крит-скиллами + медленными дорогими спеллами"},
  "Cast on Elemental Ailment (ур.14)": {energy:"10/Power на Freeze, 1/Power на Shock и Ignite", note:"Пейринг с айлмент-скиллами"},
  "Cast on Minion Death (ур.8)": {energy:"50 базовых Energy за убийство постоянного миньона", note:"Лупы на самоубийстве миньонов"},
  "Cast on Dodge (ур.14)": {energy:"2 Energy за метр переката", note:"Билды на движении"},
  "Mirage Archer (ур.8)": {note:"Перекат → Mirage стреляет вставленными дальними атаками (−30% урона)"},
  "Blasphemy (ур.8)": {note:"Проклятия становятся аурами (60 Spirit за каждое)"},
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
    out.push("<b>Эффекты:</b><br>" + effects.join("<br>"));
  }
  if (metaSel.value !== "Нет") {
    out.push("<hr>");
    out.push(UI.metaLine(metaSel.value));
    if (meta.energy) out.push("⚡ " + meta.energy);
    if (meta.note) out.push("💡 " + meta.note);
    out.push(`Мета-камни накапливают <a href="meta-gems.md">Energy</a> от своего триггера; на максимуме все вставленные заклинания срабатывают автоматически.`);
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

## Чем это лучше плоского каталога

- **Совместимость тегов — ошибка №1**: калькулятор блокирует саппорты, чьих тегов нет у скилла.
- **Бюджет сокетов** — видно, когда превышен лимит 3/4/5.
- **Множитель стоимости** — стек дорогих саппортов (Unleash ×1.3, Spell Echo ×1.4) — классическая ловушка мана-голода.
- **Математика урона** — саппорты дают *more*-множители; здесь они суммируются по типам (в игре применяются мультипликативно — инструмент для сравнения, не точный DPS-метр).

Связанное: [skill-gems.md](skill-gems.md) · [support-gems.md](support-gems.md) · [meta-gems.md](meta-gems.md) · [uncut-tiers.md](uncut-tiers.md)
