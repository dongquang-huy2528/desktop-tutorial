<!DOCTYPE html>
<html lang="vi">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Gửi bạn một cái ôm</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Quicksand:wght@500;700&family=Pacifico&display=swap" rel="stylesheet">
<style>
:root{--bg:#fff0f3;--card:#ffffff;--ink:#4a2c3a;--muted:#8a6577;--accent:#ff5c8a;--soft:#ffd6e2;--shadow:rgba(255,92,138,.22);color-scheme:light;
box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px)}
@media (prefers-color-scheme:dark){:root:not([data-theme="light"]){--bg:#241621;--card:#34202f;--ink:#ffe9f0;--muted:#d5a9bb;--accent:#ff7da3;--soft:#5a2c47;--shadow:rgba(0,0,0,.45);color-scheme:dark}}
:root[data-theme="dark"]{--bg:#241621;--card:#34202f;--ink:#ffe9f0;--muted:#d5a9bb;--accent:#ff7da3;--soft:#5a2c47;--shadow:rgba(0,0,0,.45);color-scheme:dark}
html{scroll-padding-top:env(safe-area-inset-top,0px);scroll-behavior:smooth}
*{box-sizing:border-box}
body{margin:0;background:var(--bg);color:var(--ink);font-family:'Quicksand','Be Vietnam Pro',system-ui,sans-serif;font-weight:500;line-height:1.6}
main{max-width:640px;margin:0 auto;padding:24px 18px 60px}
.hero{text-align:center;padding:18px 0 8px}
.hero .bear{font-size:72px;display:inline-block;animation:sway 3s ease-in-out infinite}
h1{font-family:'Pacifico','Quicksand',cursive;font-weight:400;font-size:clamp(28px,8vw,40px);margin:6px 0;color:var(--accent);line-height:1.3}
.sub{color:var(--muted);margin:0}
.card{background:var(--card);border-radius:24px;padding:22px 20px;margin-top:18px;box-shadow:0 10px 30px var(--shadow)}
.card h2{margin:0 0 6px;font-size:20px}
.card p.hint{margin:0 0 14px;color:var(--muted);font-size:15px}
button{font:inherit;font-weight:700;cursor:pointer;border:0;border-radius:999px;padding:13px 24px;background:var(--accent);color:#fff;box-shadow:0 6px 16px var(--shadow);transition:transform .15s}
button:active{transform:scale(.95)}
button.ghost{background:var(--soft);color:var(--ink);box-shadow:none}
.center{text-align:center}
.msg{min-height:84px;margin-top:16px;font-size:18px;text-align:center;display:flex;align-items:center;justify-content:center;padding:6px 4px}
.msg.show{animation:fade .6s ease}
.count{font-size:15px;color:var(--muted);margin-top:12px;min-height:24px}
.breathe{display:flex;flex-direction:column;align-items:center;gap:18px}
.orb{width:120px;height:120px;border-radius:50%;background:radial-gradient(circle at 35% 30%,#fff7,var(--accent));display:flex;align-items:center;justify-content:center;color:#fff;font-weight:700;text-align:center;font-size:15px;margin:40px 0 28px}
.orb.run{animation:breath 8s ease-in-out infinite}
.coupons{display:grid;grid-template-columns:repeat(2,1fr);gap:12px}
.coupon{background:var(--soft);border-radius:18px;padding:16px 12px;min-height:110px;text-align:center;cursor:pointer;border:2px dashed var(--accent);display:flex;align-items:center;justify-content:center;font-size:15px;color:var(--ink);transition:transform .2s;user-select:none}
.coupon:active{transform:scale(.96)}
.coupon.open{background:var(--accent);color:#fff;border-style:solid}
.letter{white-space:pre-wrap;font-size:17px}
.sign{text-align:right;margin-top:10px;color:var(--accent);font-family:'Pacifico',cursive}
details{margin-top:26px;color:var(--muted)}
summary{cursor:pointer;text-align:center;font-size:14px}
label{display:block;margin:12px 0 4px;font-size:14px}
input,select,textarea{width:100%;font:inherit;padding:10px 12px;border-radius:12px;border:2px solid var(--soft);background:var(--card);color:var(--ink)}
.row{display:flex;gap:8px;margin-top:12px}
.row input{flex:1}
.heart{position:fixed;pointer-events:none;font-size:24px;z-index:50;animation:floatup 1.6s ease-out forwards}
footer{text-align:center;margin-top:34px;color:var(--muted);font-size:14px}
@keyframes sway{0%,100%{transform:rotate(-6deg)}50%{transform:rotate(6deg)}}
@keyframes fade{from{opacity:0;transform:translateY(8px)}to{opacity:1;transform:none}}
@keyframes breath{0%,100%{transform:scale(1)}50%{transform:scale(1.7)}}
@keyframes floatup{from{opacity:1;transform:translate(0,0) scale(.8)}to{opacity:0;transform:translate(var(--dx),-170px) scale(1.4)}}
@media (prefers-reduced-motion:reduce){.hero .bear,.orb.run{animation:none}.heart{display:none}}
</style>
</head>
<body>
<main>
  <div class="hero">
    <div class="bear">🧸</div>
    <h1 id="title">Gửi người thương</h1>
    <p class="sub">Hôm nay nếu có chút buồn, hãy ghé đây một lát nhé.</p>
  </div>

  <section class="card" id="letterCard" hidden>
    <h2>💌 Thư riêng</h2>
    <div class="letter" id="letter"></div>
    <div class="sign" id="sign"></div>
  </section>

  <section class="card">
    <h2>Bấm khi thấy buồn</h2>
    <p class="hint">Mỗi lần bấm là một lời nhắn nhỏ gửi riêng cho bạn.</p>
    <div class="center"><button id="btnMsg">Gửi mình một lời an ủi 💗</button></div>
    <div class="msg" id="msg">…</div>
  </section>

  <section class="card center">
    <h2>Ôm một cái nào 🤗</h2>
    <p class="hint">Bấm bao nhiêu lần cũng được, không giới hạn.</p>
    <button id="btnHug">Ôm!</button>
    <div class="count" id="count"></div>
  </section>

  <section class="card breathe">
    <div style="text-align:center"><h2>Hít thở cùng nhau 🌿</h2>
    <p class="hint">Hít vào 4 giây, thở ra 4 giây. Làm vài vòng sẽ nhẹ hơn.</p></div>
    <div class="orb" id="orb">Sẵn sàng?</div>
    <button class="ghost" id="btnBreath">Bắt đầu thở</button>
  </section>

  <section class="card">
    <h2>🍀 Thẻ may mắn</h2>
    <p class="hint">Chạm vào từng thẻ để xem hôm nay may mắn được bao gì nhé.</p>
    <div class="coupons" id="coupons"></div>
  </section>

  <details>
    <summary>Dành cho người gửi: tạo link riêng 💞</summary>
    <div class="card">
      <label for="fTo">Tên người nhận</label><input id="fTo" placeholder="Ví dụ: Lan">
      <label for="fFrom">Tên của bạn</label><input id="fFrom" placeholder="Ví dụ: Minh">
      <label for="fX">Cách xưng hô (bạn → người nhận)</label>
      <select id="fX"><option value="tc">Tớ – Cậu</option><option value="ae">Anh – Em</option><option value="ea">Em – Anh</option></select>
      <label for="fMsg">Lời nhắn riêng (không bắt buộc)</label><textarea id="fMsg" rows="4" placeholder="Viết vài dòng từ trái tim…"></textarea>
      <div class="row"><button id="btnLink" type="button">Tạo link</button><input id="fOut" readonly placeholder="Link sẽ hiện ở đây"><button class="ghost" id="btnCopy" type="button">Chép</button></div>
    </div>
  </details>

  <footer>Làm bằng cả tấm lòng 💗</footer>
</main>

<script>
(function(){
var q=new URLSearchParams(location.search);
var to=(q.get('to')||'').trim(), from=(q.get('from')||'').trim(), custom=(q.get('msg')||'').trim();
var xh={tc:['tớ','cậu'],ae:['anh','em'],ea:['em','anh']};
var pr=xh[q.get('x')]||xh.tc;
function cap(s){return s.charAt(0).toUpperCase()+s.slice(1)}
function fill(t){return t.replace(/\{Me\}/g,cap(pr[0])).replace(/\{You\}/g,cap(pr[1])).replace(/\{me\}/g,pr[0]).replace(/\{you\}/g,pr[1])}
var $=function(id){return document.getElementById(id)};

if(to){$('title').textContent='Gửi '+to; document.title='Gửi '+to+' một cái ôm'}
if(custom||from){
  $('letterCard').hidden=false;
  $('letter').textContent=custom||fill('{Me} ở đây với {you}.');
  if(from)$('sign').textContent='— '+from;
}

var msgs=[
"{Me} biết hôm nay có thể không dễ dàng, nhưng {you} đã cố gắng rất nhiều rồi. {Me} tự hào về {you}.",
"Buồn cũng không sao. {You} cứ khóc, cứ giận, cứ im lặng. {Me} vẫn ở đây.",
"Dù ngày hôm nay tệ đến đâu, cuối ngày vẫn có {me} đang nghĩ về {you}.",
"{You} không cần phải mạnh mẽ mọi lúc. Dựa vào {me} một chút nhé.",
"Chuyện gì rồi cũng sẽ qua. Còn {me} thì ở lại.",
"Nếu {you} mệt thì nghỉ một chút. Thế giới chờ được, {me} cũng chờ được.",
"{You} quan trọng với {me} hơn bất cứ điều gì đang làm {you} buồn lúc này.",
"Hít sâu một hơi. Uống một ngụm nước. Rồi nhớ rằng {you} được yêu thương rất nhiều.",
"Nụ cười của {you} là điều {me} thích nhất. Khi nào sẵn sàng thì cười lại nhé, {me} không vội.",
"Dù {you} có làm sai điều gì, {me} vẫn thương {you}. Chỉ vậy thôi.",
"Hôm nay {you} đã đủ tốt rồi. Thật đấy.",
"Gửi {you} một cái ôm thật chặt, qua màn hình cũng được."
];
var last=-1;
function burst(x,y,n){
  var em=['💗','💖','💕','🌸','✨'];
  for(var i=0;i<n;i++){
    var s=document.createElement('span');
    s.className='heart';s.textContent=em[Math.floor(Math.random()*em.length)];
    s.style.left=(x-12+Math.random()*30-15)+'px';s.style.top=(y-12)+'px';
    s.style.setProperty('--dx',(Math.random()*120-60)+'px');
    s.style.animationDelay=(i*70)+'ms';
    s.addEventListener('animationend',function(){this.remove()});
    document.body.appendChild(s);
  }
}
function centerOf(el){var r=el.getBoundingClientRect();return [r.left+r.width/2,r.top+r.height/2]}

$('btnMsg').addEventListener('click',function(e){
  var i;do{i=Math.floor(Math.random()*msgs.length)}while(i===last&&msgs.length>1);
  last=i;var m=$('msg');m.classList.remove('show');void m.offsetWidth;
  m.textContent=fill(msgs[i]);m.classList.add('show');
  var c=centerOf(e.currentTarget);burst(c[0],c[1],6);
});

var hugs=0;
try{hugs=parseInt(localStorage.getItem('hugs'),10)||0}catch(e){}
var notes={1:'Đã ôm rồi nè 🤗',5:'Thêm chút vitamin yêu thương nữa nào',10:'Pin yêu thương đã đầy một nửa 🔋',20:'Đầy 100% rồi nhé!',30:'Ôm nhiều thế này thì hết buồn rồi chứ? 😊'};
function showCount(){
  var t=hugs?('Đã ôm '+hugs+' cái'):'';
  var keys=Object.keys(notes).map(Number).filter(function(k){return k<=hugs});
  if(keys.length)t+=' · '+notes[keys[keys.length-1]];
  $('count').textContent=t;
}
showCount();
$('btnHug').addEventListener('click',function(e){
  hugs++;try{localStorage.setItem('hugs',hugs)}catch(err){}
  showCount();var c=centerOf(e.currentTarget);burst(c[0],c[1],8);
});

var timer=null,inhale=true;
$('btnBreath').addEventListener('click',function(){
  var orb=$('orb'),b=this;
  if(timer){clearInterval(timer);timer=null;orb.classList.remove('run');orb.textContent='Sẵn sàng?';b.textContent='Bắt đầu thở';return}
  inhale=true;orb.textContent='Hít vào…';orb.classList.add('run');b.textContent='Dừng lại';
  timer=setInterval(function(){inhale=!inhale;orb.textContent=inhale?'Hít vào…':'Thở ra…'},4000);
});

var cp=[
"🍜 Bao ăn",
"🧋 Bao uống nước",
"🎬 Bao xem phim",
"🎡 Bao đi chơi",
"🎁 Bao quà bất ngờ",
"🌟 Bao cả một ngày"
];
var box=$('coupons');
cp.forEach(function(t,i){
  var d=document.createElement('div');d.className='coupon';d.textContent='🍀 Thẻ số '+(i+1);
  d.addEventListener('click',function(e){
    var open=d.classList.toggle('open');
    d.textContent=open?fill(t):'🍀 Thẻ số '+(i+1);
    if(open){burst(e.clientX,e.clientY,4)}
  });
  box.appendChild(d);
});

$('btnLink').addEventListener('click',function(){
  var p=new URLSearchParams();
  if($('fTo').value.trim())p.set('to',$('fTo').value.trim());
  if($('fFrom').value.trim())p.set('from',$('fFrom').value.trim());
  p.set('x',$('fX').value);
  if($('fMsg').value.trim())p.set('msg',$('fMsg').value.trim());
  $('fOut').value=location.origin+location.pathname+'?'+p.toString();
});
$('btnCopy').addEventListener('click',function(){
  var o=$('fOut');if(!o.value)return;
  o.select();
  try{navigator.clipboard.writeText(o.value)}catch(e){try{document.execCommand('copy')}catch(e2){}}
  this.textContent='Đã chép';var b=this;setTimeout(function(){b.textContent='Chép'},1500);
});
})();
</script>
</body>
</html>
