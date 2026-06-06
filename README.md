# testbazar<!DOCTYPE html>
<html lang="bn">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>History MCQ Quiz</title>
<style>
body{font-family:Arial,sans-serif;background:#f4f4f4;max-width:800px;margin:auto;padding:20px}
.card{background:#fff;padding:20px;border-radius:10px;box-shadow:0 0 10px rgba(0,0,0,.1)}
button{display:block;width:100%;margin:8px 0;padding:10px}
.correct{background:#c8f7c5}
.wrong{background:#f7c5c5}
#nextBtn{display:none}
</style>
</head>
<body>
<div class="card" id="quiz"></div>

<script>
const questions=[
{q:"বাংলায় মুদ্রিত প্রথম সংবাদপত্র কোনটি?",opts:["সমাচার দর্পণ","সংবাদ প্রভাকর","সোমপ্রকাশ","বঙ্গদর্শন"],ans:0,exp:"সমাচার দর্পণ ১৮১৮ সালে প্রকাশিত হয়।"},
{q:"হিন্দু কলেজ প্রতিষ্ঠিত হয় কত সালে?",opts:["১৮১৭","১৮২০","১৮৩৫","১৮৫৭"],ans:0,exp:"হিন্দু কলেজ ১৮১৭ সালে প্রতিষ্ঠিত হয়।"},
{q:"বিধবা বিবাহ আইন পাশ হয় কত সালে?",opts:["১৮৫৬","১৮৫৭","১৮৬১","১৮৪৮"],ans:0,exp:"১৮৫৬ সালে বিধবা বিবাহ আইন পাশ হয়।"},
{q:"সাঁওতাল বিদ্রোহ শুরু হয় কত সালে?",opts:["১৮৫৫","১৮৫৭","১৮৩১","১৮৭৫"],ans:0,exp:"১৮৫৫ সালে সাঁওতাল বিদ্রোহ শুরু হয়।"},
{q:"আনন্দমঠ গ্রন্থের রচয়িতা কে?",opts:["রবীন্দ্রনাথ","বঙ্কিমচন্দ্র","বিদ্যাসাগর","মাইকেল"],ans:1,exp:"বঙ্কিমচন্দ্র চট্টোপাধ্যায় আনন্দমঠ রচনা করেন।"},
{q:"বঙ্গভঙ্গ হয় কত সালে?",opts:["১৯০৫","১৯০৬","১৯১১","১৯০১"],ans:0,exp:"১৯০৫ সালে বঙ্গভঙ্গ কার্যকর হয়।"},
{q:"জালিয়ানওয়ালা বাগ হত্যাকাণ্ড সংঘটিত হয় কত সালে?",opts:["১৯১৫","১৯১৯","১৯২০","১৯২২"],ans:1,exp:"১৩ এপ্রিল ১৯১৯ সালে।"},
{q:"সীমান্ত গান্ধী নামে কে পরিচিত?",opts:["গান্ধীজি","গফ্ফর খান","নেহরু","আজাদ"],ans:1,exp:"খান আবদুল গফ্ফর খান।"},
{q:"ভারত স্বাধীনতা লাভ করে কত সালে?",opts:["১৯৪৫","১৯৪৬","১৯৪৭","১৯৫০"],ans:2,exp:"১৫ আগস্ট ১৯৪৭।"},
{q:"ভারতের প্রথম গভর্নর জেনারেল কে?",opts:["কর্নওয়ালিস","ওয়ারেন হেস্টিংস","বেন্টিঙ্ক","ডালহৌসি"],ans:1,exp:"ওয়ারেন হেস্টিংস ছিলেন প্রথম গভর্নর জেনারেল।"}
];

let current=0,score=0;

function showQuestion(){
const q=questions[current];
document.getElementById("quiz").innerHTML=`
<h2>ইতিহাস MCQ টেস্ট</h2>
<p>প্রশ্ন ${current+1}/${questions.length}</p>
<h3>${q.q}</h3>
${q.opts.map((o,i)=>`<button onclick="check(${i})" id="b${i}">${o}</button>`).join("")}
<p id="exp"></p>
<button id="nextBtn" onclick="nextQ()">পরের প্রশ্ন</button>`;
}

function check(i){
const q=questions[current];
for(let j=0;j<q.opts.length;j++){
document.getElementById("b"+j).disabled=true;
if(j===q.ans) document.getElementById("b"+j).classList.add("correct");
}
if(i!==q.ans) document.getElementById("b"+i).classList.add("wrong");
if(i===q.ans) score++;
document.getElementById("exp").innerHTML="<b>ব্যাখ্যা:</b> "+q.exp;
document.getElementById("nextBtn").style.display="block";
}

function nextQ(){
current++;
if(current<questions.length) showQuestion();
else{
document.getElementById("quiz").innerHTML=`
<h2>ফলাফল</h2>
<h1>${score}/${questions.length}</h1>
<p>আপনার স্কোর: ${Math.round(score/questions.length*100)}%</p>`;
}
}
showQuestion();
</script>
</body>
</html>
