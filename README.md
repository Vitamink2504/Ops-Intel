<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>OPS INTELLIGENCE</title>
<link href="https://fonts.googleapis.com/css2?family=Figtree:wght@400;500;600;700&display=swap" rel="stylesheet">
<style>
:root{
  --deep:#0B3C5D; --deep2:#082C45; --sky:#5FB4E5; --sky-l:#E3F2FB;
  --bg:#F5F7F9; --card:#FFFFFF; --ink:#262B30; --mute:#6A737C; --line:#E2E7EB;
  --ok:#1E8E5A; --warn:#C27A0E; --bad:#B8322F; --r:10px;
}
*{box-sizing:border-box;margin:0}
html,body{height:100%}
body{font-family:Figtree,system-ui,-apple-system,"Segoe UI",sans-serif;background:var(--bg);color:var(--ink);font-size:15px;line-height:1.5}
button,input,select,textarea{font:inherit;color:inherit}
:focus-visible{outline:2px solid var(--sky);outline-offset:2px}
h1{font-size:1.5rem;font-weight:700}
h2{font-size:1.05rem;font-weight:600}
.mute{color:var(--mute);font-size:.88rem}
.login{min-height:100%;display:grid;place-items:center;padding:20px;background:linear-gradient(160deg,var(--deep2),var(--deep))}
.login-box{background:#fff;border-radius:14px;padding:32px;width:100%;max-width:400px}
.brand{font-weight:700;letter-spacing:.04em;color:var(--deep);font-size:1.15rem}
.login-box h1{margin:18px 0 4px}
.roles{display:grid;gap:10px;margin:20px 0}
.role{display:block;text-align:left;width:100%;padding:12px 14px;border:1px solid var(--line);border-radius:var(--r);background:#fff;cursor:pointer}
.role:hover{border-color:var(--sky);background:var(--sky-l)}
.role b{display:block;color:var(--deep)}
.shell{display:grid;grid-template-columns:230px 1fr;min-height:100%}
.side{background:var(--deep);color:#DCEBF5;padding:20px 12px;display:flex;flex-direction:column;gap:4px;position:sticky;top:0;height:100vh}
.side .brand{color:#fff;padding:0 10px 16px}
.nav{background:none;border:0;color:inherit;text-align:left;padding:10px 12px;border-radius:8px;cursor:pointer;width:100%}
.nav:hover{background:rgba(255,255,255,.08)}
.nav.on{background:var(--sky);color:var(--deep2);font-weight:600}
.who{margin-top:auto;padding:10px;font-size:.85rem;border-top:1px solid rgba(255,255,255,.15)}
.who button{margin-top:8px;background:none;border:1px solid rgba(255,255,255,.35);color:#fff;border-radius:8px;padding:6px 10px;cursor:pointer}
main{padding:28px;max-width:1100px;width:100%}
.top{display:flex;justify-content:space-between;align-items:end;gap:12px;flex-wrap:wrap;margin-bottom:20px}
.grid{display:grid;gap:16px}
.g4{grid-template-columns:repeat(4,1fr)}
.g2{grid-template-columns:1.2fr 1fr}
.card{background:var(--card);border:1px solid var(--line);border-radius:var(--r);padding:18px}
.stat b{display:block;font-size:1.8rem;color:var(--deep);line-height:1.1}
.stat.alert b{color:var(--bad)}
.bar{display:grid;grid-template-columns:110px 1fr 42px;gap:10px;align-items:center;margin:10px 0;font-size:.9rem}
.track{height:10px;background:var(--sky-l);border-radius:6px;overflow:hidden}
.fill{height:100%;background:var(--deep);border-radius:6px}
.fill.lo{background:var(--warn)}
.tw{overflow-x:auto}
table{width:100%;border-collapse:collapse;font-size:.9rem}
th,td{text-align:left;padding:10px 8px;border-bottom:1px solid var(--line);vertical-align:top}
th{color:var(--mute);font-weight:500;font-size:.82rem}
.tag{display:inline-block;padding:2px 9px;border-radius:20px;font-size:.78rem;background:var(--sky-l);color:var(--deep)}
.tag.High,.tag.Overdue{background:#F8E1E0;color:var(--bad)}
.tag.Medium{background:#FBEBD0;color:var(--warn)}
.btn{background:var(--deep);color:#fff;border:0;border-radius:8px;padding:10px 18px;cursor:pointer;font-weight:600}
.btn:hover{background:var(--deep2)}
.btn.alt{background:#fff;color:var(--deep);border:1px solid var(--deep)}
.btn.sm{padding:5px 10px;font-size:.82rem}
.form{display:grid;gap:16px}
.row{display:grid;grid-template-columns:repeat(auto-fit,minmax(170px,1fr));gap:14px}
label{display:grid;gap:5px;font-weight:500;font-size:.9rem}
input,select,textarea{border:1px solid #C9D2D9;border-radius:8px;padding:10px;background:#fff;width:100%}
textarea{min-height:76px;resize:vertical}
fieldset{border:1px solid var(--line);border-radius:var(--r);padding:14px;display:grid;gap:10px}
legend{padding:0 6px;font-weight:600;color:var(--deep)}
.mode{display:flex;gap:10px;align-items:flex-start;padding:10px;border:1px solid var(--line);border-radius:8px;cursor:pointer;font-weight:400}
.mode input{width:auto;margin-top:4px}
.mode.sel{border-color:var(--deep);background:var(--sky-l)}
.err{color:var(--bad);font-size:.82rem}
.chk{display:flex;gap:8px;align-items:center;font-weight:400}
.chk input{width:auto}
.toast{position:fixed;bottom:20px;left:50%;transform:translateX(-50%);background:var(--deep2);color:#fff;padding:12px 20px;border-radius:10px;z-index:9}
@media(max-width:820px){
  .shell{grid-template-columns:1fr}
  .side{position:static;height:auto;flex-direction:row;flex-wrap:wrap;padding:10px;align-items:center}
  .side .brand{padding:0 8px;width:100%}
  .nav{width:auto;padding:8px 12px}
  .who{margin:0;border:0;width:100%;display:flex;gap:10px;align-items:center;justify-content:space-between}
  .who button{margin:0}
  main{padding:18px 14px}
  .g4{grid-template-columns:1fr 1fr}.g2{grid-template-columns:1fr}
  .bar{grid-template-columns:90px 1fr 38px}
}
</style>
</head>
<body>
<div id="app"></div>
<script>
const DEPTS=[
 {n:'Kitchen',exp:14,sub:13,score:86},{n:'Inventory',exp:3,sub:3,score:91},
 {n:'Bar',exp:6,sub:5,score:78},{n:'Front of House',exp:18,sub:14,score:72},
 {n:'Housekeeping',exp:5,sub:5,score:88},{n:'Administration',exp:4,sub:3,score:84}];
let incidents=[
 {id:'INC-0041',cat:'Food safety',dept:'Kitchen',sev:'High',status:'Investigation',desc:'Walk-in chiller reading 8°C during PM shift.'},
 {id:'INC-0040',cat:'Customer complaints',dept:'Front of House',sev:'Medium',status:'Action Required',desc:'Table 12 waited 35 min for mains.'},
 {id:'INC-0039',cat:'Inventory discrepancies',dept:'Bar',sev:'Medium',status:'Under Review',desc:'Gin variance of 3 bottles against reconciliation.'},
 {id:'INC-0038',cat:'Equipment breakdown',dept:'Kitchen',sev:'Low',status:'Resolved',desc:'Combi oven door seal replaced.'}];
let actions=[
 {id:'ACT-012',title:'Service engineer to inspect chiller',dept:'Kitchen',owner:'Operations Manager',due:'2026-11-22',status:'In Progress'},
 {id:'ACT-011',title:'Retrain floor team on ticket-time checks',dept:'Front of House',owner:'Floor Manager',due:'2026-11-18',status:'Overdue'}];
let reports=[
 {id:'R-301',date:'2026-11-19',dept:'Kitchen',mode:'Standard',author:'A. Mensah (Line Cook)',text:'Oven 2 slow to heat. Prep finished on time.'},
 {id:'R-302',date:'2026-11-19',dept:'Front of House',mode:'Confidential',author:'K. Osei (Waiter)',text:'Concern about unequal table allocation on weekends.'},
 {id:'R-303',date:'2026-11-19',dept:'Bar',mode:'Anonymous',author:null,text:'Ice machine leaking behind the bar for three days.'}];
const ME={name:'Ama Boateng',dept:'Kitchen',job:'Sous Chef',id:'EMP-0107'};
const submitted=new Set(); let draft={}; let user=null; let page='';

const esc=s=>String(s??'').replace(/[&<>"']/g,c=>({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#39;'}[c]));
const $=s=>document.querySelector(s);
const today=new Date().toISOString().slice(0,10);
const isMgr=()=>user&&user.role!=='employee';
function toast(m){const t=document.createElement('div');t.className='toast';t.setAttribute('role','status');t.textContent=m;document.body.appendChild(t);setTimeout(()=>t.remove(),2600)}
function go(p){page=p;draw()}
function login(role,label){user={role,label};go(role==='employee'?'home':'dash')}
function logout(){user=null;draw()}

function draw(){
  const a=$('#app');
  if(!user){a.innerHTML=`<div class="login"><div class="login-box">
    <div class="brand">OPS INTELLIGENCE</div>
    <h1>Sign in</h1>
    <p class="mute">Prototype: choose a role to preview. Real sign-in, a database and server-side permissions are not included in this file.</p>
    <div class="roles">
      <button class="role" onclick="login('employee','Employee')"><b>Employee</b>Submit shift reports and view your history</button>
      <button class="role" onclick="login('manager','Department Manager')"><b>Department Manager</b>Reviews reports; cannot identify confidential authors</button>
      <button class="role" onclick="login('admin','Super Admin')"><b>Super Admin</b>Full view, including permitted identity reveal</button>
    </div></div></div>`;return}
  const nav=isMgr()?[['dash','Dashboard'],['incidents','Incidents'],['actions','Action Centre'],['archive','Report Archive']]
    :[['home','Home'],['submit','Submit report'],['history','My history']];
  a.innerHTML=`<div class="shell"><aside class="side"><div class="brand">OPS INTELLIGENCE</div>
    ${nav.map(([k,l])=>`<button class="nav ${page===k?'on':''}" onclick="go('${k}')">${l}</button>`).join('')}
    ${user.role==='employee'?`<button class="nav ${page==='anon'?'on':''}" onclick="go('anon')">Anonymous report</button>`:''}
    <div class="who">${esc(isMgr()?user.label:ME.name)}<br><span style="opacity:.7">${esc(user.label)}</span><br><button onclick="logout()">Sign out</button></div></aside>
    <main id="view"></main></div>`;
  ({home,submit:()=>form('standard'),anon:()=>form('anonymous'),history,dash,incidents:incView,actions:actView,archive:arcView})[page]();
}

function home(){
  const due=!submitted.has(today+'AM');
  $('#view').innerHTML=`<div class="top"><div><h1>Good day, ${esc(ME.name.split(' ')[0])}</h1><p class="mute">${esc(ME.job)}, ${esc(ME.dept)} · ${esc(ME.id)}</p></div></div>
  <div class="grid g2"><div class="card"><h2>Today's shift report</h2>
    <p class="mute" style="margin:6px 0 14px">${due?'Your AM report has not been submitted yet.':'Your AM report is submitted. Thank you.'}</p>
    <button class="btn" onclick="go('submit')">${due?'Start report':'Submit another shift'}</button></div>
  <div class="card"><h2>Speak up safely</h2><p class="mute" style="margin:6px 0 14px">Raising problems is encouraged and is never counted against you in appraisals.</p>
    <button class="btn alt" onclick="go('anon')">Send an anonymous report</button></div></div>`;
}
function form(mode){
  const anonOnly=mode==='anonymous';
  const modes={standard:['Standard','Your name is attached. Only authorised managers can view it.'],
    confidential:['Confidential','Your identity is hidden from supervisors. Only senior staff with explicit permission can identify you, and every look-up is logged.'],
    anonymous:['Anonymous','No name or ID is stored with this report. Writing style or details may still hint at who you are, and we cannot promise absolute anonymity.']};
  const cur=draft.mode&&!anonOnly?draft.mode:mode;
  $('#view').innerHTML=`<div class="top"><div><h1>${anonOnly?'Anonymous report':'Daily shift report'}</h1><p class="mute">${anonOnly?'Not linked to your account.':esc(ME.job)+' · Kitchen template'}</p></div></div>
  <form class="form card" id="f" onsubmit="send(event,${anonOnly})" novalidate>
   <fieldset><legend>Privacy level</legend>
    ${Object.entries(modes).filter(([k])=>anonOnly?k==='anonymous':true).map(([k,[l,d]])=>`
     <label class="mode ${cur===k?'sel':''}"><input type="radio" name="mode" value="${k}" ${cur===k?'checked':''} onchange="draft.mode=this.value;form('${mode}')"><span><b>${l}</b><br><span class="mute">${d}</span></span></label>`).join('')}
   </fieldset>
   <div class="row">
    <label>Date<input type="date" name="date" value="${today}" required></label>
    <label>Shift<select name="shift"><option>AM</option><option>PM</option></select></label>
    <label>Department<select name="dept">${DEPTS.map(d=>`<option ${d.n===ME.dept?'selected':''}>${d.n}</option>`).join('')}</select></label>
   </div>
   <fieldset><legend>Service numbers</legend><div class="row">
    <label>Orders received<input type="number" min="0" name="recv" required></label>
    <label>Orders completed<input type="number" min="0" name="done" required></label>
    <label>Orders delayed<input type="number" min="0" name="late" value="0"></label>
    <label>Orders remade<input type="number" min="0" name="remade" value="0"></label>
    <label>Food wastage (kg)<input type="number" min="0" step=".1" name="waste"></label>
   </div>
   <label class="chk"><input type="checkbox" name="open"> Opening preparation completed</label>
   <label class="chk"><input type="checkbox" name="hyg"> Hygiene and sanitation checks passed</label>
   <label>Equipment status<select name="equip"><option>All working</option><option>Minor fault</option><option>Breakdown</option></select></label></fieldset>
   <label>What went well?<textarea name="well"></textarea></label>
   <label>What went wrong?<textarea name="wrong" required></textarea></label>
   <label>What needs management attention?<textarea name="attn"></textarea></label>
   <label>Recommendations<textarea name="rec"></textarea></label>
   <div id="errs" class="err" role="alert"></div>
   <div style="display:flex;gap:10px;flex-wrap:wrap"><button class="btn" type="submit">Submit report</button>
   <button class="btn alt" type="button" onclick="saveDraft()">Save draft</button></div>
  </form>`;
  const f=$('#f');
  Object.entries(draft).forEach(([k,v])=>{const e=f.elements[k];if(e&&k!=='mode')e.type==='checkbox'?e.checked=v:e.value=v});
}
function saveDraft(){const f=$('#f');new FormData(f).forEach((v,k)=>draft[k]=v);['open','hyg'].forEach(k=>draft[k]=f.elements[k].checked);toast('Draft saved');}
function send(e,anonOnly){
  e.preventDefault();const f=e.target,d=Object.fromEntries(new FormData(f)),er=[];
  if(!d.recv)er.push('Enter the number of orders received.');
  if(!d.done)er.push('Enter the number of orders completed.');
  if(+d.done>+d.recv)er.push('Orders completed cannot exceed orders received.');
  if(!d.wrong.trim())er.push('Describe what went wrong, or write "Nothing".');
  const key=anonOnly?null:d.date+d.shift;
  if(key&&submitted.has(key))er.push('A report for this date and shift was already submitted. Use an amendment to correct it.');
  if(er.length){$('#errs').innerHTML=er.map(esc).join('<br>');return}
  if(key)submitted.add(key);
  const id='R-'+(304+reports.length-3);
  reports.unshift({id,date:d.date,dept:d.dept,mode:anonOnly?'Anonymous':{standard:'Standard',confidential:'Confidential',anonymous:'Anonymous'}[d.mode],
    author:(anonOnly||d.mode==='anonymous')?null:ME.name+' ('+ME.job+')',text:d.wrong,mine:!(anonOnly||d.mode==='anonymous')});
  draft={};$('#view').innerHTML=`<div class="card"><h1>Report submitted</h1><p class="mute" style="margin:8px 0 16px">Reference ${esc(id)} · ${esc(d.date)} ${esc(d.shift)}. Thank you for reporting honestly.</p><button class="btn" onclick="go('${anonOnly?'home':'history'}')">${anonOnly?'Back to home':'View my history'}</button></div>`;
}
function history(){
  const mine=reports.filter(r=>r.mine);
  $('#view').innerHTML=`<div class="top"><h1>My history</h1></div><div class="card tw"><table><tr><th>Ref</th><th>Date</th><th>Privacy</th><th>Summary</th></tr>
  ${mine.length?mine.map(r=>`<tr><td>${r.id}</td><td>${r.date}</td><td><span class="tag">${r.mode}</span></td><td>${esc(r.text)}</td></tr>`).join(''):'<tr><td colspan="4" class="mute">No reports yet. Anonymous reports never appear here by design.</td></tr>'}</table></div>`;
}

function dash(){
  const exp=DEPTS.reduce((s,d)=>s+d.exp,0),sub=DEPTS.reduce((s,d)=>s+d.sub,0);
  const open=incidents.filter(i=>!['Resolved','Closed'].includes(i.status)).length;
  const over=actions.filter(a=>a.status==='Overdue').length;
  $('#view').innerHTML=`<div class="top"><div><h1>Operations overview</h1><p class="mute">Today · demo data</p></div></div>
  <div class="grid g4">
   <div class="card stat"><b>${sub}/${exp}</b>Reports submitted</div>
   <div class="card stat"><b>${Math.round(sub/exp*100)}%</b>Compliance</div>
   <div class="card stat"><b>${open}</b>Unresolved incidents</div>
   <div class="card stat ${over?'alert':''}"><b>${over}</b>Overdue actions</div></div>
  <div class="grid g2" style="margin-top:16px">
   <div class="card"><h2>Department performance</h2>${DEPTS.map(d=>`<div class="bar"><span>${d.n}</span><div class="track"><div class="fill ${d.score<80?'lo':''}" style="width:${d.score}%"></div></div><b>${d.score}</b></div>`).join('')}
    <p class="mute">Scores come from configurable KPIs, not report counts.</p></div>
   <div class="card"><h2>Outstanding reports</h2>${DEPTS.filter(d=>d.sub<d.exp).map(d=>`<div class="bar" style="grid-template-columns:1fr auto"><span>${d.n}</span><span class="tag Medium">${d.exp-d.sub} missing</span></div>`).join('')}
    <h2 style="margin-top:18px">Recurring issues</h2><p class="mute" style="margin-top:6px">Chiller temperature (3 reports this week), Table service delays (5), Bar ice machine (2).</p></div></div>`;
}
const STAT=['New','Under Review','Investigation','Action Required','Resolved','Closed'];
function incView(){
  $('#view').innerHTML=`<div class="top"><h1>Incident management</h1></div><div class="card tw"><table>
  <tr><th>Ref</th><th>Category</th><th>Dept</th><th>Severity</th><th>Description</th><th>Status</th><th></th></tr>
  ${incidents.map((i,n)=>`<tr><td>${i.id}</td><td>${esc(i.cat)}</td><td>${esc(i.dept)}</td><td><span class="tag ${i.sev}">${i.sev}</span></td><td>${esc(i.desc)}</td>
   <td><select aria-label="Status for ${i.id}" onchange="incidents[${n}].status=this.value;toast('${i.id} updated')">${STAT.map(s=>`<option ${s===i.status?'selected':''}>${s}</option>`).join('')}</select></td>
   <td><button class="btn sm" onclick="toAction(${n})">Create action</button></td></tr>`).join('')}</table></div>`;
}
function toAction(n){const i=incidents[n];actions.unshift({id:'ACT-0'+(13+actions.length-2),title:'Follow up: '+i.desc,dept:i.dept,owner:'Unassigned',due:today,status:'Pending'});toast('Action created');go('actions')}
const ASTAT=['Pending','In Progress','Awaiting Review','Completed','Overdue'];
function actView(){
  $('#view').innerHTML=`<div class="top"><h1>Action Centre</h1></div><div class="card tw"><table>
  <tr><th>Ref</th><th>Action</th><th>Department</th><th>Owner</th><th>Due</th><th>Status</th></tr>
  ${actions.map((a,n)=>`<tr><td>${a.id}</td><td>${esc(a.title)}</td><td>${esc(a.dept)}</td><td>${esc(a.owner)}</td><td>${a.due}</td>
   <td><select aria-label="Status for ${a.id}" onchange="actions[${n}].status=this.value;toast('${a.id} updated')">${ASTAT.map(s=>`<option ${s===a.status?'selected':''}>${s}</option>`).join('')}</select></td></tr>`).join('')}</table></div>`;
}
let revealed=new Set(),q='';
function arcView(){
  const list=reports.filter(r=>(r.text+r.dept).toLowerCase().includes(q.toLowerCase()));
  $('#view').innerHTML=`<div class="top"><h1>Report archive</h1><input style="max-width:260px" placeholder="Search report text" value="${esc(q)}" oninput="q=this.value;arcView();this.focus()" aria-label="Search"></div>
  <div class="card tw"><table><tr><th>Ref</th><th>Date</th><th>Dept</th><th>Privacy</th><th>Submitted by</th><th>Report</th></tr>
  ${list.map(r=>{let who;
    if(r.mode==='Anonymous')who='<span class="mute">Not recorded</span>';
    else if(r.mode==='Confidential'&&!revealed.has(r.id))who=user.role==='admin'?`<button class="btn sm alt" onclick="revealed.add('${r.id}');toast('Identity reveal logged');arcView()">Reveal (logged)</button>`:'<span class="mute">Protected</span>';
    else who=esc(r.author);
    return `<tr><td>${r.id}</td><td>${r.date}</td><td>${esc(r.dept)}</td><td><span class="tag">${r.mode}</span></td><td>${who}</td><td>${esc(r.text)}</td></tr>`}).join('')}</table></div>
  <p class="mute" style="margin-top:10px">Demo: a Department Manager sees confidential authors as protected; only Super Admin can reveal.</p>`;
}
draw();
</script>
</body>
</html>
