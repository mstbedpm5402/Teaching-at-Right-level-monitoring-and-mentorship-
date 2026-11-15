<!doctype html>
<html lang="en">
<head>
<meta charset="utf8">
<meta name="viewport" content="width=device-width,initial-scale=1,viewport-fit=cover">
<title>TaRL Mentor Academy</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Bricolage+Grotesque:opsz,wght@12..96,500;12..96,700&family=Inter:wght@400;500;600&display=swap" rel="stylesheet">
<style>
:root{
  --bg:#F2F6F4; --surface:#FFFFFF; --surface2:#E8EFEC; --fg:#14201C; --muted:#52645E; --line:#D3DED9;
  --accent:#0E6B58; --accent-fg:#FFFFFF; --accent-soft:#D6EBE5;
  --c0:#46605A; --c1:#C0432E; --c2:#B9860B; --c3:#2B63B8; --c4:#2E8B4E; --c5:#7A4FA3;
  --ok:#1F7A45; --bad:#B3321F; --hl:#FFF1B8;
  --fd:'Bricolage Grotesque','Inter',system-ui,sans-serif; --fb:'Inter',system-ui,-apple-system,'Segoe UI',sans-serif;
}
@media (prefers-color-scheme:dark){:root:not([data-theme="light"]){
  --bg:#0D1513; --surface:#151F1C; --surface2:#1C2925; --fg:#E7F0EC; --muted:#9DB0A9; --line:#2A3A35;
  --accent:#4FC3A6; --accent-fg:#06201A; --accent-soft:#16352E;
  --c0:#8FB0A6; --c1:#EE7B66; --c2:#E5B84A; --c3:#6FA1EE; --c4:#5CC27E; --c5:#B28BDA;
  --ok:#5CC27E; --bad:#F08B79; --hl:#4A4220; color-scheme:dark}}
:root[data-theme="dark"]{
  --bg:#0D1513; --surface:#151F1C; --surface2:#1C2925; --fg:#E7F0EC; --muted:#9DB0A9; --line:#2A3A35;
  --accent:#4FC3A6; --accent-fg:#06201A; --accent-soft:#16352E;
  --c0:#8FB0A6; --c1:#EE7B66; --c2:#E5B84A; --c3:#6FA1EE; --c4:#5CC27E; --c5:#B28BDA;
  --ok:#5CC27E; --bad:#F08B79; --hl:#4A4220; color-scheme:dark}
*{box-sizing:border-box}
body{background:var(--bg);color:var(--fg);font:16px/1.65 var(--fb);margin:0;padding-left:max(16px,env(safe-area-inset-left,0px));padding-right:max(16px,env(safe-area-inset-right,0px));padding-block:0}
body::before{content:"";position:fixed;inset:0 0 auto;height:env(safe-area-inset-top,0px);z-index:40;background:var(--surface)}
a{color:var(--accent)}
button,select,textarea,input{font:inherit;color:inherit}
:focus-visible{outline:3px solid var(--accent);outline-offset:2px}
.top{position:sticky;top:env(safe-area-inset-top,0px);z-index:30;background:var(--surface);border-bottom:1px solid var(--line);margin:0 calc(-1*max(16px,env(safe-area-inset-left,0px)));padding:10px max(16px,env(safe-area-inset-right,0px)) 10px max(16px,env(safe-area-inset-left,0px));display:flex;align-items:center;gap:12px}
.brand{font:700 18px/1.1 var(--fd);letter-spacing:-.01em;display:flex;gap:10px;align-items:center;cursor:pointer;background:none;border:0;padding:0;text-align:left}
.dots{display:grid;grid-template-columns:repeat(2,9px);gap:2px}.dots i{width:9px;height:9px;border-radius:2px;display:block}
.dots i:nth-child(1){background:var(--c1)}.dots i:nth-child(2){background:var(--c2)}.dots i:nth-child(3){background:var(--c3)}.dots i:nth-child(4){background:var(--c4)}
.prog{flex:1;display:flex;align-items:center;gap:10px;min-width:0;justify-content:flex-end}
.bar{height:8px;background:var(--surface2);border-radius:99px;overflow:hidden;flex:0 1 220px;width:100%}
.bar>b{display:block;height:100%;background:var(--accent);width:0;transition:width .3s}
.pct{font-size:13px;color:var(--muted);font-variant-numeric:tabular-nums;white-space:nowrap}
.btn{background:var(--accent);color:var(--accent-fg);border:0;border-radius:8px;padding:9px 16px;font-weight:600;cursor:pointer;min-height:40px}
.btn.ghost{background:transparent;color:var(--accent);border:1px solid var(--accent)}
.btn.sm{padding:5px 12px;min-height:32px;font-size:14px}
.btn:disabled{opacity:.45;cursor:not-allowed}
#menuBtn{display:none}
.shell{display:grid;grid-template-columns:300px minmax(0,1fr);gap:32px;max-width:1240px;margin:0 auto;padding-block:24px 150px}
nav#side{position:sticky;top:calc(64px + env(safe-area-inset-top,0px));align-self:start;max-height:calc(100vh - 150px);overflow:auto;font-size:14px}
nav#side details{border-top:1px solid var(--line);padding:6px 0}
nav#side summary{cursor:pointer;font-weight:600;padding:6px 0;list-style:none;display:flex;gap:8px;align-items:flex-start}
nav#side summary::-webkit-details-marker{display:none}
.sw{width:10px;height:10px;border-radius:3px;margin-top:6px;flex:none}
nav#side a.li, nav#side button.li{display:flex;gap:8px;padding:6px 8px 6px 18px;text-decoration:none;color:var(--fg);border-radius:6px;line-height:1.35;width:100%;background:none;border:0;text-align:left;cursor:pointer;font:inherit}
nav#side a.li:hover, nav#side button.li:hover{background:var(--surface2)}
nav#side a.li[aria-current="page"]{background:var(--accent-soft);font-weight:600}
.ck{width:16px;height:16px;border:1.5px solid var(--line);border-radius:50%;flex:none;margin-top:2px;display:grid;place-items:center;font-size:10px}
.ck.on{background:var(--ok);border-color:var(--ok);color:#fff}
main{min-width:0;max-width:760px}
.crumb{font-size:13px;color:var(--muted);text-transform:uppercase;letter-spacing:.08em;display:flex;gap:8px;align-items:center;margin-bottom:6px}
h1{font:700 clamp(28px,5vw,40px)/1.12 var(--fd);letter-spacing:-.02em;margin:0 0 6px;text-wrap:balance}
h3{font:700 21px/1.25 var(--fd);margin:34px 0 8px;text-wrap:balance}
h4{font:700 14px/1.3 var(--fb);text-transform:uppercase;letter-spacing:.07em;margin:0 0 6px}
p{margin:0 0 14px}ul,ol{padding-left:22px;margin:0 0 16px}li{margin-bottom:6px}
.meta{color:var(--muted);font-size:14px;margin-bottom:22px}
.callout{background:var(--accent-soft);border-radius:10px;padding:14px 16px;margin:20px 0}
.callout p:last-child{margin:0}
.callout.warn{background:var(--surface2);border:1px solid var(--line)}
.tw{overflow-x:auto;margin:16px 0;border:1px solid var(--line);border-radius:10px;background:var(--surface)}
table{border-collapse:collapse;width:100%;min-width:560px;font-size:14px;line-height:1.5}
th,td{text-align:left;vertical-align:top;padding:10px 12px;border-bottom:1px solid var(--line)}
th{background:var(--surface2);font-size:12px;text-transform:uppercase;letter-spacing:.06em}
tr:last-child td{border-bottom:0}td.rh{font-weight:600}
.widget,.practice{background:var(--surface);border:1px solid var(--line);border-radius:12px;padding:16px;margin:22px 0}
.widget h4,.practice h4{color:var(--accent)}
input[type="text"], input[type="email"], select, textarea{width:100%;background:var(--bg);border:1px solid var(--line);border-radius:8px;padding:10px;margin:6px 0 12px}
.cert{border:3px double var(--accent);border-radius:12px;padding:28px 20px;text-align:center;background:var(--surface);margin:20px 0}
.cert h2{font:700 30px var(--fd);margin:6px 0}.cert .nm{font:700 28px var(--fd);border-bottom:2px solid var(--line);display:inline-block;padding:0 18px 4px;margin:10px 0}
.sr{position:absolute;width:1px;height:1px;overflow:hidden;clip:rect(0 0 0 0)}
@media (max-width:900px){
  .shell{grid-template-columns:minmax(0,1fr)}
  #menuBtn{display:inline-block}
  nav#side{display:none;position:fixed;inset:0;top:calc(58px + env(safe-area-inset-top,0px));max-height:none;background:var(--bg);z-index:29;padding:12px max(16px,env(safe-area-inset-right,0px)) 160px max(16px,env(safe-area-inset-left,0px))}
  body.menu nav#side{display:block}
  .pct{display:none}.bar{flex:1}
}
</style>
</head>
<body>
<header class="top">
  <button id="menuBtn" class="btn ghost sm" aria-expanded="false" aria-controls="side">Menu</button>
  <button class="brand" id="brandBtn" aria-label="Course home"><span class="dots" aria-hidden="true"><i></i><i></i><i></i><i></i></span><span>TaRL Mentor Academy</span></button>
  <div class="prog"><span class="pct" id="pct">0%</span><div class="bar" role="progressbar" aria-label="Course progress" id="pbar"><b id="pfill"></b></div></div>
</header>
<div class="shell">
  <nav id="side" aria-label="Course outline"></nav>
  <main id="main" tabindex="-1"></main>
</div>

<script>
const $=(s,r=document)=>r.querySelector(s), $$=(s,r=document)=>[...r.querySelectorAll(s)];
const esc=s=>String(s).replace(/[&<>"]/g,c=>({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;'}[c]));

const KEY='tarl-mentor-academy-v2';
let S={done:{},notes:{},scores:{},students:[],adminUnlocked:false};
try{const r=localStorage.getItem(KEY);if(r)S=Object.assign(S,JSON.parse(r))}catch(e){}
const save=()=>{try{localStorage.setItem(KEY,JSON.stringify(S))}catch(e){}};

// Mock default content for navigation
const VIEWS = {
  home: {
    title: "Welcome to TaRL Mentor Academy",
    render: () => `
      <div class="hero">
        <div class="crumb"><span>Professional Development</span></div>
        <h1>Teaching at the Right Level (TaRL) Mentor Academy</h1>
        <p class="lead">Accelerating foundational literacy and numeracy through evidence-based mentoring, assessment, and level-based classroom groupings.</p>
        
        <div style="display:flex;gap:12px;margin:20px 0;">
          <button class="btn" onclick="app.showReg()">Register Student Profile</button>
          <button class="btn ghost" onclick="app.showAdminLogin()">Admin Portal</button>
        </div>
      </div>
    `
  },
  register: {
    title: "Student Registration",
    render: () => `
      <h2>Student & Participant Registration</h2>
      <p>Register your details to track your TaRL module progression, test scores, and certification.</p>
      <div class="widget">
        <form onsubmit="app.handleReg(event)">
          <label>Full Name:</label>
          <input type="text" id="regName" required placeholder="e.g., Mohammed Tura">
          
          <label>School / Cluster / Organization:</label>
          <input type="text" id="regSchool" required placeholder="e.g., Addis Ababa Primary Education">
          
          <label>Teaching Grade / Role:</label>
          <input type="text" id="regGrade" required placeholder="e.g., Grade 3-4 Teacher / Mentor">
          
          <label>Email / Phone:</label>
          <input type="text" id="regContact" required placeholder="e.g., mstbedpm@gmail.com">
          
          <button type="submit" class="btn" style="margin-top:12px;">Save Registration</button>
        </form>
      </div>
    `
  },
  admin: {
    title: "Admin Portal",
    render: () => {
      if(!S.adminUnlocked) {
        return `
          <h2>Admin Authentication</h2>
          <p>Please enter the administrator security code to access participant records.</p>
          <div class="widget">
            <form onsubmit="app.handleAdminLogin(event)">
              <label>Admin Code:</label>
              <input type="password" id="adminPin" required placeholder="Enter 8-digit secure code">
              <button type="submit" class="btn" style="margin-top:12px;">Unlock Portal</button>
            </form>
          </div>
        `;
      }
      return `
        <h2>Admin Dashboard: Registered Students</h2>
        <p>Overview of all registered students and program participants in local storage.</p>
        <div class="tw">
          <table>
            <thead>
              <tr><th>Name</th><th>School / Organization</th><th>Role / Grade</th><th>Contact</th><th>Registered Date</th></tr>
            </thead>
            <tbody>
              ${S.students.length === 0 ? '<tr><td colspan="5">No registered students found yet.</td></tr>' : 
                S.students.map(st => `<tr><td><b>${esc(st.name)}</b></td><td>${esc(st.school)}</td><td>${esc(st.grade)}</td><td>${esc(st.contact)}</td><td>${st.date}</td></tr>`).join('')}
            </tbody>
          </table>
        </div>
        <button class="btn ghost sm" onclick="app.lockAdmin()" style="margin-top:16px;">Lock Admin Portal</button>
      `;
    }
  }
};

const app = {
  currentView: 'home',
  init() {
    this.renderNav();
    this.renderMain();
    this.updateProgress();
  },
  renderNav() {
    const nav = $('#side');
    nav.innerHTML = `
      <div style="padding:10px 12px;">
        <button class="li" onclick="app.setView('home')"><b>🏠 Course Overview</b></button>
        <button class="li" onclick="app.setView('register')"><b>📝 Student Registration</b></button>
        <button class="li" onclick="app.setView('admin')"><b>🔒 Admin Portal</b></button>
      </div>
    `;
  },
  renderMain() {
    const main = $('#main');
    const v = VIEWS[this.currentView] || VIEWS.home;
    main.innerHTML = v.render();
  },
  setView(v) {
    this.currentView = v;
    this.renderMain();
    window.scrollTo(0,0);
  },
  showReg() { this.setView('register'); },
  showAdminLogin() { this.setView('admin'); },
  handleReg(e) {
    e.preventDefault();
    const name = $('#regName').value.trim();
    const school = $('#regSchool'].value.trim();
    const grade = $('#regGrade').value.trim();
    const contact = $('#regContact').value.trim();
    
    S.students.push({ name, school, grade, contact, date: new Date().toLocaleDateString() });
    save();
    alert('Registration successful! Welcome, ' + name + '.');
    this.setView('home');
  },
  handleAdminLogin(e) {
    e.preventDefault();
    const pin = $('#adminPin').value.trim();
    // Hidden passcode check: 54025402
    if(pin === '54025402') {
      S.adminUnlocked = true;
      save();
      this.renderMain();
    } else {
      alert('Incorrect administrator passcode.');
    }
  },
  lockAdmin() {
    S.adminUnlocked = false;
    save();
    this.renderMain();
  },
  updateProgress() {
    $('#pfill').style.width = '15%';
    $('#pct').innerText = '15%';
  }
};

$('#brandBtn').onclick = () => app.setView('home');
$('#menuBtn').onclick = () => document.body.classList.toggle('menu');

app.init();
</script>
</body>
</html>
