# dkwlqrkrhtlvedk
플레이 ai
<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>최악의 조합 배틀</title>
<style>
*{box-sizing:border-box}
body{
 margin:0;padding:22px 14px 40px;color:#f7f5ff;
 font-family:Arial,sans-serif;
 background:radial-gradient(ellipse at top left,#40203d,transparent 40%),
 radial-gradient(ellipse at top right,#17384a,transparent 35%),#11111b
}
main{width:min(1000px,100%);margin:auto}
header{text-align:center;margin:12px 0 26px}
.eyebrow{color:#ff64ad;font-size:12px;letter-spacing:2px;font-weight:bold}
h1{font-size:clamp(32px,6vw,55px);margin:14px 0}
h1 span{color:#ff64ad}
header p{color:#b7b4ce;line-height:1.7}
.panel{background:#1d1d2c;border:1px solid #ffffff20;border-radius:20px;padding:18px;margin-bottom:17px}
.title{font-size:13px;color:#b7b4ce;font-weight:bold;margin-bottom:15px}
.draw-grid,.fighters{display:grid;grid-template-columns:1fr 1fr;gap:13px}
.draw-box{background:#292940;border-radius:15px;padding:14px}
.draw-box h3{font-size:15px;margin:0 0 12px}
.slot{min-height:65px;display:flex;align-items:center;justify-content:center;text-align:center;padding:12px;background:#141420;border:1px dashed #ffffff40;border-radius:12px;line-height:1.6;font-weight:bold}
.spinning{animation:shake .12s infinite;color:#ffe477}
@keyframes shake{50%{transform:scale(.97);opacity:.65}}
button{border:0;border-radius:12px;padding:13px 15px;font-weight:bold;font-size:15px;cursor:pointer}
button:disabled{opacity:.4;cursor:not-allowed}
button:hover:not(:disabled){filter:brightness(1.13)}
.drawbtn{width:100%;margin-top:10px;background:#393954;color:white}
.primary{background:linear-gradient(100deg,#ff64ad,#ff9c78);color:#25121d}
.secondary{background:#34344d;color:white;border:1px solid #ffffff20}
.full{width:100%;margin-top:13px;padding:16px}
.fighter{position:relative;overflow:hidden}
.you{border-top:3px solid #68e8ff}
.enemy{border-top:3px solid #ff64ad}
.badge{font-size:11px;color:#b7b4ce;font-weight:bold}
.avatar{text-align:center;font-size:66px;margin:15px 0 6px}
.fname{text-align:center;font-size:22px;font-weight:900;overflow-wrap:anywhere}
.meta{text-align:center;color:#b7b4ce;font-size:12px;line-height:1.6;margin:9px 0 17px}
.hptext{display:flex;justify-content:space-between;font-size:12px;margin-bottom:7px}
.hpbar{height:11px;background:#101019;border-radius:20px;overflow:hidden}
.hpfill{height:100%;width:100%;background:linear-gradient(90deg,#5ee6a6,#b7f77b);transition:width .3s}
.hpfill.low{background:linear-gradient(90deg,#ff4f72,#ff9b6a)}
.stats{display:grid;grid-template-columns:repeat(3,1fr);gap:7px;margin-top:14px}
.stat{text-align:center;background:#ffffff0c;border-radius:9px;padding:10px 3px}
.stat b{display:block;font-size:17px}
.stat span{font-size:10px;color:#b7b4ce}
.arena{text-align:center;padding:20px 10px;border-radius:14px;background:linear-gradient(120deg,#30203b,#182d3b)}
.vs{font-size:30px;color:#ffe477;font-weight:1000}
#message{font-weight:bold;line-height:1.7;margin-top:8px}
.buttons{display:flex;gap:8px;margin-top:13px}
.buttons button{flex:1}
.log{display:flex;flex-direction:column;gap:8px;max-height:270px;overflow:auto}
.entry{padding:10px 12px;background:#ffffff09;border-left:3px solid #77738f;border-radius:8px;font-size:13px;line-height:1.6}
.entry.special{border-color:#ffe477}
.entry.good{border-color:#68e8ff}
.entry.bad{border-color:#ff64ad}
.entry.win{border-color:#76f2b0}
.hint{color:#b7b4ce;font-size:12px;line-height:1.6;margin:12px 2px 0}
.fighter.attack{animation:attack .32s ease}
.fighter.hit{animation:hit .32s ease}
.fighter.heal{animation:heal .45s ease}
.fighter.winner{box-shadow:0 0 25px #76f2b066}
@keyframes attack{50%{transform:translateY(-7px) scale(1.02)}}
@keyframes hit{0%,100%{transform:translateX(0)}25%{transform:translateX(-7px)}75%{transform:translateX(7px)}}
@keyframes heal{50%{filter:brightness(1.7)}}
.damage-float{position:absolute;top:35%;left:50%;transform:translate(-50%,-50%);font-size:26px;font-weight:900;color:#ff718e;text-shadow:0 2px 8px #000;pointer-events:none;animation:floatup .8s forwards;z-index:5}
.damage-float.good{color:#76f2b0}
@keyframes floatup{to{opacity:0;transform:translate(-50%,-100px)}}
.empty{text-align:center;color:#b7b4ce;padding:15px;font-size:13px}
footer{text-align:center;color:#8e8ba8;font-size:11px;line-height:1.8}
@media(max-width:650px){
 body{padding:16px 10px 30px}
 .draw-grid,.fighters{grid-template-columns:1fr}
 .buttons{flex-direction:column}
 .panel{padding:14px}
}
</style>
</head>
<body>
<main>
<header>
 <div class="eyebrow">THE MOST CURSED COMBO BATTLE</div>
 <h1>최악의 조합 <span>배틀</span></h1>
 <p>돌림판으로 황당한 캐릭터를 뽑고 싸워 보자!<br>
 AI API 없이 무료로 실행되는 1인용 전투 게임</p>
</header>

<section class="panel">
 <div class="title">🎰 STEP 1 · 직업 / 초능력 / 약점 뽑기</div>
 <div class="draw-grid">
  <div class="draw-box">
   <h3>🔵 내 캐릭터</h3>
   <div class="slot" id="pJobSlot">직업을 뽑아 줘!</div>
   <button class="drawbtn" id="pJobBtn">🎭 직업 뽑기</button>
   <div class="slot" id="pPowerSlot" style="margin-top:9px">초능력을 뽑아 줘!</div>
   <button class="drawbtn" id="pPowerBtn">⚡ 초능력 뽑기</button>
   <div class="slot" id="pWeakSlot" style="margin-top:9px">약점을 뽑아 줘!</div>
   <button class="drawbtn" id="pWeakBtn">💀 약점 뽑기</button>
  </div>
  <div class="draw-box">
   <h3>🔴 상대 캐릭터</h3>
   <div class="slot" id="eJobSlot">상대 직업을 뽑아 줘!</div>
   <button class="drawbtn" id="eJobBtn">🎭 직업 뽑기</button>
   <div class="slot" id="ePowerSlot" style="margin-top:9px">상대 초능력을 뽑아 줘!</div>
   <button class="drawbtn" id="ePowerBtn">⚡ 초능력 뽑기</button>
   <div class="slot" id="eWeakSlot" style="margin-top:9px">상대 약점을 뽑아 줘!</div>
   <button class="drawbtn" id="eWeakBtn">💀 약점 뽑기</button>
  </div>
 </div>
 <button class="primary full" id="spinBoth">🎰 양쪽 캐릭터 전부 뽑기</button>
 <p class="hint">직업, 초능력, 약점을 각각 뽑으면 전투를 시작할 수 있어.</p>
</section>

<section class="fighters">
 <div class="panel fighter you" id="pCard">
  <div class="badge">PLAYER · 내 캐릭터</div>
  <div class="avatar" id="pAvatar">❔</div>
  <div class="fname" id="pName">미선택</div>
  <div class="meta" id="pMeta">직업 · 초능력 · 약점</div>
  <div class="hptext"><span>체력</span><b id="pHpText">100 / 100</b></div>
  <div class="hpbar"><div class="hpfill" id="pHpBar"></div></div>
  <div class="stats">
   <div class="stat"><b id="pAtk">—</b><span>공격력</span></div>
   <div class="stat"><b id="pDef">—</b><span>방어력</span></div>
   <div class="stat"><b id="pSp">—</b><span>특수력</span></div>
  </div>
 </div>
 <div class="panel fighter enemy" id="eCard">
  <div class="badge">CPU · 상대 캐릭터</div>
  <div class="avatar" id="eAvatar">❔</div>
  <div class="fname" id="eName">미선택</div>
  <div class="meta" id="eMeta">상대를 뽑아 줘</div>
  <div class="hptext"><span>체력</span><b id="eHpText">100 / 100</b></div>
  <div class="hpbar"><div class="hpfill" id="eHpBar"></div></div>
  <div class="stats">
   <div class="stat"><b id="eAtk">—</b><span>공격력</span></div>
   <div class="stat"><b id="eDef">—</b><span>방어력</span></div>
   <div class="stat"><b id="eSp">—</b><span>특수력</span></div>
  </div>
 </div>
</section>

<section class="panel" style="margin-top:17px">
 <div class="title">⚔️ STEP 2 · 전투</div>
 <div class="arena">
  <div class="vs">PLAYER VS CPU</div>
  <div id="message">두 캐릭터를 뽑고 전투를 시작해!</div>
 </div>
 <div class="buttons">
  <button class="primary" id="start" disabled>⚔️ 전투 시작</button>
  <button class="secondary" id="next" disabled>다음 턴 진행</button>
  <button class="secondary" id="rematch" disabled>🔄 새 대결</button>
 </div>
</section>

<section class="panel">
 <div class="title">📜 전투 기록</div>
 <div class="log" id="log"><div class="empty">아직 전투 기록이 없어.</div></div>
</section>

<footer>최악의 조합 배틀 · HTML / CSS / JavaScript<br>
외부 서버 및 AI API 없이 브라우저에서 작동합니다.</footer>
</main>

<script>
const jobs = [
 ["은퇴한 마왕","😈",17,12,18],
 ["편의점 알바생","🧑‍💼",10,11,14],
 ["감자 농부","🥔",13,12,15],
 ["전국 꼴찌 히어로","🦸",12,10,17],
 ["잠만 자는 탐정","🕵️",11,15,18],
 ["드래곤 치과 의사","🐉",18,14,13],
 ["우주 택배 기사","👨‍🚀",15,11,16],
 ["고양이 왕국 대사","🐱",12,16,15],
 ["말하는 감자","🥔",9,18,16],
 ["마법 학교 청소부","🧹",13,16,14],
 ["프로게이머","🎮",15,10,18],
 ["유령 아파트 관리인","👻",14,13,17],
 ["전설의 김밥 장인","🍙",12,14,18],
 ["뱀파이어 헌터","🧛",17,12,15],
 ["월요일 수호자","📅",16,15,10],
 ["무인도 배달원","🏝️",14,13,16],
 ["전설의 청소 로봇","🤖",14,17,13],
 ["초보 용사","🗡️",13,11,16],
 ["마법 감자 상인","🪄",12,13,19],
 ["수상한 헬스장 관장","💪",18,15,9]
];

const powers = [
 ["화염구를 발사한다","attack"],
 ["시간을 3초 멈춘다","special"],
 ["감자 폭격을 일으킨다","attack"],
 ["순간이동으로 공격을 피한다","defend"],
 ["라면을 먹고 체력을 회복한다","heal"],
 ["번개 강타를 날린다","attack"],
 ["분신을 만들어 혼란시킨다","special"],
 ["슬리퍼 유도탄을 발사한다","attack"],
 ["절대 방패를 펼친다","defend"],
 ["상대의 기술을 복사한다","special"],
 ["트로트 충격파를 날린다","attack"],
 ["미래를 예측해 공격을 피한다","defend"],
 ["에너지를 흡수한다","special"],
 ["거대 주먹으로 내려친다","attack"],
 ["비눗방울 보호막을 만든다","defend"],
 ["필살기 충전으로 힘을 모은다","special"],
 ["박수 폭발을 일으킨다","attack"],
 ["유령 동료를 소환한다","special"],
 ["중력을 뒤집는다","special"],
 ["민망함 공격으로 상대를 얼린다","special"],
 ["방귀 추진으로 돌진한다","attack"],
 ["무한 양말을 던진다","attack"],
 ["숙제를 소환해 상대를 압박한다","special"],
 ["모든 음식을 1도 더 맛있게 만든다","heal"],
 ["손가락 레이저 포인터를 쏜다","attack"],
 ["상대에게 갑자기 퀴즈를 낸다","special"],
 ["무작위로 몸집이 커진다","special"],
 ["고양이에게 지원을 요청한다","special"],
 ["전투 음악을 크게 틀어 사기를 올린다","heal"],
 ["자신의 그림자와 자리를 바꾼다","defend"]
];

const weaknesses = [
 ["고양이를 보면 굳어 버린다","stun"],
 ["공격할 때마다 천 원이 사라진다","miss"],
 ["중요한 순간에 딸꾹질한다","miss"],
 ["배고프면 적에게 존댓말을 한다","weak"],
 ["비 오는 날 능력이 반대로 작동한다","weak"],
 ["능력 사용 후 트로트 춤을 춘다","stun"],
 ["칭찬받으면 10분 동안 기절한다","stun"],
 ["신발 한 짝이 자주 사라진다","weak"],
 ["거짓말하면 머리 위에 자막이 뜬다","weak"],
 ["필살기 이름을 외치다 시간을 낭비한다","miss"],
 ["비둘기를 무서워한다","stun"],
 ["체력이 낮으면 졸음이 쏟아진다","weak"],
 ["능력을 쓰면 재채기가 나온다","miss"],
 ["돈을 보면 줍느라 멈춘다","stun"],
 ["중요한 순간에 전화가 온다","miss"],
 ["자기 능력을 자주 잊어버린다","weak"],
 ["싸우기 전에 스트레칭을 10초 한다","miss"],
 ["상대가 박수 치면 춤을 춘다","stun"],
 ["자기 소개를 너무 길게 한다","miss"],
 ["승리 직전에 자랑하다가 방심한다","weak"],
 ["배터리가 5% 남은 상태다","weak"],
 ["왼쪽으로만 회피할 수 있다","weak"],
 ["무서우면 방어력이 반으로 줄어든다","weak"],
 ["전투 중 간식을 찾으러 간다","miss"],
 ["공격할 때마다 자기 이름을 외친다","miss"],
 ["비밀을 지키려 하면 큰 소리로 말한다","weak"],
 ["모든 버튼을 반대로 누르고 싶어진다","weak"],
 ["자기 필살기를 무서워한다","weak"],
 ["재채기하면 능력이 무작위로 발동한다","miss"],
 ["상대의 말장난에 웃음을 참지 못한다","stun"]
];

const taunts = [
 "심판이 규칙집을 다시 펼쳐 봤다.",
 "관중석에서 '저게 맞아?'라는 소리가 들린다.",
 "양쪽 모두 자신감만큼은 최종 보스급이다.",
 "전투보다 캐릭터 설정이 더 혼란스럽다.",
 "누군가 이 경기를 학교 축제의 전설로 기록했다.",
 "두 캐릭터 모두 집에 가고 싶어 하는 것 같다."
];

let player = {job:null,power:null,weakness:null,hp:100,maxHp:100,atk:0,def:0,sp:0,guarding:false,stunned:false};
let enemy = {job:null,power:null,weakness:null,hp:100,maxHp:100,atk:0,def:0,sp:0,guarding:false,stunned:false};
let round=0, running=false, busy=false, finished=false;
const $ = id => document.getElementById(id);
const pick = arr => arr[Math.floor(Math.random()*arr.length)];

function isComplete(c){return !!(c.job&&c.power&&c.weakness)}
function allComplete(){return isComplete(player)&&isComplete(enemy)}
function updateButtons(){
 const lock=busy||running||finished;
 ['pJobBtn','pPowerBtn','pWeakBtn','eJobBtn','ePowerBtn','eWeakBtn','spinBoth'].forEach(id=>$(id).disabled=lock);
 $('start').disabled=!allComplete()||running||busy||finished;
 $('next').disabled=!running||busy;
 $('rematch').disabled=!player.job||!enemy.job||busy;
}
function recalc(c){
 if(!isComplete(c))return;
 c.hp=100;c.maxHp=100;
 c.atk=c.job.atk+Math.floor(Math.random()*7);
 c.def=c.job.def+Math.floor(Math.random()*7);
 c.sp=c.job.sp+Math.floor(Math.random()*7);
 c.guarding=false;c.stunned=false;
}
function spinSlot(element,finalText,values,duration=1150){
 return new Promise(resolve=>{
  const start=performance.now();let last=0;
  element.classList.add('spinning');
  function frame(now){
   const elapsed=now-start, progress=Math.min(1,elapsed/duration);
   const interval=35+Math.pow(progress,2)*210;
   if(now-last>=interval){element.textContent=pick(values);last=now}
   if(progress<1){requestAnimationFrame(frame)}else{element.textContent=finalText;element.classList.remove('spinning');resolve()}
  }
  requestAnimationFrame(frame);
 });
}
async function drawAttribute(side,type){
 if(busy||running||finished)return;
 const c=side==='p'?player:enemy;
 if(c[type])return;
 busy=true;updateButtons();
 const prefix=side==='p'?'p':'e';
 const slot=$(prefix+(type==='job'?'Job':type==='power'?'Power':'Weak')+'Slot');
 let item,values;
 if(type==='job'){
  item=pick(jobs);values=jobs.map(x=>x[0]);
  await spinSlot(slot,item[1]+' '+item[0],values);
  c.job={name:item[0],emoji:item[1],atk:item[2],def:item[3],sp:item[4]};
 }else if(type==='power'){
  item=pick(powers);values=powers.map(x=>x[0]);
  await spinSlot(slot,'⚡ '+item[0],values);
  c.power={name:item[0],kind:item[1]};
 }else{
  item=pick(weaknesses);values=weaknesses.map(x=>x[0]);
  await spinSlot(slot,'💀 '+item[0],values);
  c.weakness={name:item[0],effect:item[1]};
 }
 if(isComplete(c)){recalc(c);render(side,c)}
 $('message').textContent=allComplete()?'두 캐릭터 완성! 전투를 시작해!':(side==='p'?'내 캐릭터':'상대 캐릭터')+'의 '+(type==='job'?'직업':type==='power'?'초능력':'약점')+'을 뽑았어!';
 busy=false;updateButtons();
}
function render(side,c){
 const s=side==='p'?'p':'e';
 $(s+'Avatar').textContent=c.job?c.job.emoji:'❔';
 $(s+'Name').textContent=c.job?c.job.name:'미선택';
 $(s+'Meta').textContent=[c.power?'⚡ '+c.power.name:'초능력 미선택',c.weakness?'💀 '+c.weakness.name:'약점 미선택'].join(' · ');
 $(s+'Atk').textContent=c.atk||'—';$(s+'Def').textContent=c.def||'—';$(s+'Sp').textContent=c.sp||'—';
 updateHp(side,c);
}
function updateHp(side,c){
 const s=side==='p'?'p':'e';
 $(s+'HpText').textContent=Math.max(0,c.hp)+' / 100';
 $(s+'HpBar').style.width=Math.max(0,c.hp)+'%';
 $(s+'HpBar').classList.toggle('low',c.hp<=30);
}
function log(text,type=''){
 const box=$('log');const empty=box.querySelector('.empty');if(empty)empty.remove();
 const row=document.createElement('div');row.className='entry '+type;row.textContent=text;box.prepend(row);
}
function animate(side,type){
 const card=$(side==='p'?'pCard':'eCard');card.classList.remove('attack','hit','heal','winner');void card.offsetWidth;card.classList.add(type);
 setTimeout(()=>card.classList.remove(type),550);
}
function showDamage(side,text,good=false){
 const card=$(side==='p'?'pCard':'eCard');const el=document.createElement('div');el.className='damage-float'+(good?' good':'');el.textContent=text;card.appendChild(el);setTimeout(()=>el.remove(),850);
}
function startBattle(){
 if(!allComplete()||running||busy)return;
 running=true;finished=false;round=1;
 [player,enemy].forEach(c=>{c.hp=100;c.guarding=false;c.stunned=false});
 render('p',player);render('e',enemy);$('log').innerHTML='';
 $('message').textContent='전투 시작! 다음 턴을 눌러 전투를 진행해!';
 log('⚔️ '+player.job.name+' vs '+enemy.job.name+'! 전투 시작!','special');log(pick(taunts));updateButtons();
}
function act(a,d,as,ds){
 if(a.hp<=0||d.hp<=0)return;
 const an=as==='p'?'내 캐릭터':'상대',dn=ds==='p'?'내 캐릭터':'상대';
 if(a.stunned){a.stunned=false;log(an+'은(는) 기절해서 행동하지 못했다!','bad');return}
 if(Math.random()<.13){
  log(an+'의 약점 발동! '+a.weakness.name+'!','bad');
  if(a.weakness.effect==='stun'){a.stunned=true;log(an+'은(는) 당황해서 굳어 버렸다!','bad');return}
  if(a.weakness.effect==='miss'){log(an+'의 공격이 빗나갔다!');return}
 }
 const options=['attack','attack','defend','special'];if(a.hp<=45)options.push('heal','heal');
 const action=pick(options);
 if(action==='defend'){a.guarding=true;log(an+'은(는) 방어 자세를 취했다. 다음 피해 감소!','good');return}
 if(action==='heal'){
  const before=a.hp;a.hp=Math.min(100,a.hp+18+Math.floor(Math.random()*13));const amount=a.hp-before;
  animate(as,'heal');showDamage(as,'+'+amount,true);log(an+'은(는) 회복 기술로 HP '+amount+' 회복!','good');return;
 }
 if(action==='special'&&a.power.kind==='heal'){
  const before=a.hp;a.hp=Math.min(100,a.hp+20);const amount=a.hp-before;animate(as,'heal');showDamage(as,'+'+amount,true);
  log(an+'의 특수 능력! '+a.power.name+'. HP '+amount+' 회복!','special');return;
 }
 if(action==='special'&&a.power.kind==='defend'){a.guarding=true;log(an+'의 특수 능력! '+a.power.name+'. 방어 태세!','special');return}
 if(action==='special'&&a.power.kind==='special'&&Math.random()<.55){
  const damage=Math.max(5,Math.floor(a.sp*.8));d.hp=Math.max(0,d.hp-damage);d.stunned=true;animate(as,'attack');animate(ds,'hit');showDamage(ds,'-'+damage);
  log(an+'의 특수 능력! '+a.power.name+'! '+dn+'에게 '+damage+' 피해, 기절 효과!','special');return;
 }
 const special=action==='special';let damage=Math.max(5,Math.round((special?a.sp+10:a.atk+Math.floor(Math.random()*9))-d.def*.4));
 const critical=Math.random()<.15;if(critical)damage=Math.round(damage*1.6);
 if(d.guarding){damage=Math.max(1,Math.floor(damage*.45));d.guarding=false;log(dn+'의 방어로 피해가 감소했다!','good')}
 d.hp=Math.max(0,d.hp-damage);animate(as,'attack');animate(ds,'hit');showDamage(ds,'-'+damage);
 log(an+'의 '+(special?a.power.name:critical?'치명타 공격':'공격')+'! '+dn+'에게 '+damage+' 피해!'+(critical?' 💥 치명타!':''),critical?'special':'');
}
function finish(){
 if(player.hp>0&&enemy.hp>0)return false;
 running=false;finished=true;
 const result=player.hp<=0&&enemy.hp<=0?'무승부!':player.hp>0?'🏆 내 캐릭터 승리!':'💀 상대 캐릭터 승리!';
 $('message').textContent=result;log(result,'win');
 if(player.hp>0) $('pCard').classList.add('winner');if(enemy.hp>0)$('eCard').classList.add('winner');
 updateButtons();return true;
}
function nextTurn(){
 if(!running||busy)return;
 log('— '+round+'턴 —','special');
 if(Math.random()<.5){act(player,enemy,'p','e');if(enemy.hp>0)act(enemy,player,'e','p')}
 else{act(enemy,player,'e','p');if(player.hp>0)act(player,enemy,'p','e')}
 updateHp('p',player);updateHp('e',enemy);
 if(player.hp<=0||enemy.hp<=0){finish();return}
 if(round>=15){
  running=false;finished=true;
  const result='15턴 종료 · 🤝 무승부!';
  $('message').textContent=result;log(result,'win');updateButtons();return;
 }
 round++;
 $('message').textContent=pick(['아직 승부는 알 수 없어!','약점이 발동하면 역전할 수도 있어!','관중들이 숨죽이며 지켜보고 있다!','다음 턴에는 어떤 일이 일어날까?']);updateButtons();
}
async function drawBoth(){
 if(busy||running||finished)return;
 for(const side of ['p','e'])for(const type of ['job','power','weakness'])await drawAttribute(side,type);
}
function rematch(){
 if(!player.job||!enemy.job||busy)return;
 running=false;finished=false;round=0;
 [player,enemy].forEach(c=>{c.hp=100;c.guarding=false;c.stunned=false});
 render('p',player);render('e',enemy);$('log').innerHTML='<div class="empty">새 대결 준비 완료!</div>';
 $('message').textContent='같은 캐릭터로 다시 대결할 수 있어!';
 $('pCard').classList.remove('winner');$('eCard').classList.remove('winner');updateButtons();
}
['pJobBtn','pPowerBtn','pWeakBtn','eJobBtn','ePowerBtn','eWeakBtn'].forEach(id=>$(id).addEventListener('click',()=>{
 const side=id[0],type=id.includes('Job')?'job':id.includes('Power')?'power':'weakness';
 drawAttribute(side,type);
}));
$('spinBoth').addEventListener('click',drawBoth);
$('start').addEventListener('click',startBattle);
$('next').addEventListener('click',nextTurn);
$('rematch').addEventListener('click',rematch);
render('p',player);render('e',enemy);updateButtons();
</script>
</body>
</html>
