# testbazar
<!DOCTYPE html>
<html lang="bn">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ভূগোল মক টেস্ট (Geography Mock Test)</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #f0f2f5;
            margin: 0;
            padding: 10px;
            display: flex;
            justify-content: center;
            box-sizing: border-box;
        }
        .quiz-wrapper {
            width: 100%;
            max-width: 600px;
            box-sizing: border-box;
        }
        h1 {
            text-align: center;
            color: #1a73e8;
            margin: 15px 0;
            font-size: 22px;
        }
        /* Login Screen */
        .start-screen {
            background-color: #fff;
            padding: 25px 15px;
            border-radius: 12px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.08);
            text-align: center;
            margin-top: 30px;
        }
        .input-field {
            width: 90%;
            max-width: 400px;
            padding: 12px;
            margin: 15px 0;
            border: 2px solid #dadce0;
            border-radius: 6px;
            font-size: 16px;
            outline: none;
            box-sizing: border-box;
        }
        .input-field:focus {
            border-color: #1a73e8;
        }
        /* Header Info (Timer & Name) */
        .exam-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: #e8f0fe;
            padding: 12px;
            border-radius: 8px;
            margin-bottom: 15px;
            font-weight: bold;
            font-size: 14px;
            color: #1c3d5a;
            position: sticky;
            top: 5px;
            z-index: 100;
            box-shadow: 0 2px 5px rgba(0,0,0,0.05);
            box-sizing: border-box;
        }
        .timer-box {
            color: #d93025;
            background: #fce8e6;
            padding: 5px 8px;
            border-radius: 4px;
            border: 1px solid #fad2cf;
            white-space: nowrap;
        }
        /* Question Cards */
        .question-card {
            background-color: #fff;
            padding: 15px;
            border-radius: 8px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.08);
            margin-bottom: 15px;
            box-sizing: border-box;
        }
        .question-text {
            font-size: 16px;
            font-weight: bold;
            color: #333;
            margin-top: 0;
            margin-bottom: 12px;
            line-height: 1.5;
            word-wrap: break-word;
        }
        .options-container {
            display: flex;
            flex-direction: column;
            gap: 10px;
        }
        .option-label {
            background-color: #f8f9fa;
            border: 1px solid #dadce0;
            border-radius: 6px;
            padding: 12px;
            font-size: 15px;
            cursor: pointer;
            display: flex;
            align-items: center;
            transition: all 0.2s ease;
            word-break: break-word;
            line-height: 1.4;
            box-sizing: border-box;
        }
        .option-label:hover {
            background-color: #f1f3f4;
        }
        .option-label input {
            margin-right: 10px;
            transform: scale(1.2);
            flex-shrink: 0;
        }
        /* Button Style */
        .btn {
            background-color: #1a73e8;
            color: white;
            border: none;
            padding: 12px 30px;
            font-size: 16px;
            border-radius: 6px;
            cursor: pointer;
            font-weight: bold;
            transition: background 0.2s;
            width: 100%;
            max-width: 300px;
        }
        .btn:hover {
            background-color: #1557b0;
        }
        /* Correct & Wrong Answer Styles */
        .option-label.correct {
            background-color: #d4edda !important;
            border-color: #c3e6cb !important;
            color: #155724 !important;
            font-weight: bold;
        }
        .option-label.wrong {
            background-color: #f8d7da !important;
            border-color: #f5c6cb !important;
            color: #721c24 !important;
        }
        /* Explanation Box */
        .explanation-box {
            margin-top: 12px;
            padding: 12px;
            background-color: #e8f0fe;
            border-left: 4px solid #1a73e8;
            border-radius: 4px;
            font-size: 14px;
            color: #3c4043;
            display: none;
            line-height: 1.5;
            word-wrap: break-word;
        }
        /* Result Dashboard */
        .result-box {
            text-align: center;
            padding: 20px 15px;
            background: #e6f4ea;
            border-radius: 8px;
            color: #137333;
            margin-bottom: 20px;
            display: none;
            box-shadow: 0 4px 10px rgba(0,0,0,0.05);
            box-sizing: border-box;
        }

        /* 📱 মোবাইলের জন্য স্পেশাল অটো-অ্যাডজাস্টমেন্ট স্ক্রিন সেটিংস */
        @media (max-width: 480px) {
            body { padding: 5px; }
            h1 { font-size: 18px; }
            .exam-header { font-size: 13px; padding: 10px; }
            .question-text { font-size: 15px; }
            .option-label { font-size: 14px; padding: 10px; }
        }
    </style>
</head>
<body>

<div class="quiz-wrapper">
    <h1>ভূগোল মক টেস্ট</h1>

    <div id="start-screen" class="start-screen">
        <h3>পরীক্ষার্থীর নাম লিখুন:</h3>
        <input type="text" id="student-name-input" class="input-field" placeholder="আপনার সম্পূর্ণ নাম..." autocomplete="off">
        <br><br>
        <button class="btn" onclick="startExam()">পরীক্ষা শুরু করো</button>
    </div>

    <div id="exam-screen" style="display: none;">
        <div class="exam-header">
            <div style="overflow: hidden; text-overflow: ellipsis; white-space: nowrap; max-width: 65%;">পরীক্ষার্থী: <span id="display-student-name" style="color: #1a73e8;"></span></div>
            <div class="timer-box">সময় বাকি: <span id="timer">10:00</span></div>
        </div>

        <div id="result-box" class="result-box">
            <h2>🎉 পরীক্ষার ফলাফল 🎉</h2>
            <p style="font-size: 16px;">পরীক্ষার্থী: <span id="res-name" style="font-weight: bold;"></span></p>
            <p style="font-size: 22px; font-weight: bold;">মোট স্কোর: <span id="score">0</span> / ১০</p>
            <p style="font-size: 14px; color: #5f6368;">নিচে আপনার উত্তরপত্র পর্যালোচনা করুন।</p>
        </div>

        <form id="quiz-form">
            <div class="question-card" data-qnum="1">
                <p class="question-text">১. পাখির পায়ের মতো বদ্বীপ দেখা যায় যে নদীর মোহানায়-</p>
                <div class="options-container">
                    <label class="option-label"><input type="radio" name="q1" value="A">(ক) মিসিসিপি-মিসৌরি</label>
                    <label class="option-label"><input type="radio" name="q1" value="B">(খ) হোয়াংহো</label>
                    <label class="option-label"><input type="radio" name="q1" value="C">(গ) ইরাবতী</label>
                    <label class="option-label"><input type="radio" name="q1" value="D">(ঘ) তাইবার</label>
                </div>
                <div class="explanation-box" id="exp-1">
                    <strong>সঠিক উত্তর: (ক) মিসিসিপি-মিসৌরি</strong><br>
                    ব্যাখ্যা: মিসিসিপি-মিসৌরি নদীর মোহানায় নদীস্রোত ও সমুদ্রস্রোতের পারস্পরিক প্রভাবে পলি সঞ্চিত হয়ে ঠিক পাখির পায়ের মতো দেখতে একটি বদ্বীপ গঠিত হয়েছে।
                </div>
            </div>

            <div class="question-card" data-qnum="2">
                <p class="question-text">২. বায়ুমণ্ডলের যে স্তরে আবহাওয়ার গোলযোগ দেখা যায় সেই স্তরটি হলো-</p>
                <div class="options-container">
                    <label class="option-label"><input type="radio" name="q2" value="A">(ক) স্ট্র্যাটোস্ফিয়ার</label>
                    <label class="option-label"><input type="radio" name="q2" value="B">(খ) মেসোস্ফিয়ার</label>
                    <label class="option-label"><input type="radio" name="q2" value="C">(গ) ট্রপোস্ফিয়ার</label>
                    <label class="option-label"><input type="radio" name="q2" value="D">(ঘ) আইনোস্ফিয়ার</label>
                </div>
                <div class="explanation-box" id="exp-2">
                    <strong>সঠিক উত্তর: (গ) ট্রপোস্ফিয়ার</strong><br>
                    ব্যাখ্যা: ট্রপোস্ফিয়ার হলো বায়ুমণ্ডলের সবচেয়ে নীচের স্তর। ধূলিকণা ও জলীয় বাষ্পের প্রায় পুরোটাই এই স্তরে থাকায় মেঘ, ঝড়, বৃষ্টি, বজ্রপাত ইত্যাদি যাবতীয় আবহাওয়াগত গোলযোগ বা অশান্ত অবস্থা এই স্তরেই ঘটে। এই কারণে একে 'ক্ষুব্ধমণ্ডল' বলা হয়।
                </div>
            </div>

            <div class="question-card" data-qnum="3">
                <p class="question-text">৩. সমুদ্রের যে স্থানে উষ্ণ ও শীতল স্রোত উভয়ে মিলিত হয় তাকে বলে-</p>
                <div class="options-container">
                    <label class="option-label"><input type="radio" name="q3" value="A">(ক) হিমানী সম্প্রপাত</label>
                    <label class="option-label"><input type="radio" name="q3" value="B">(খ) হিমশৈল</label>
                    <label class="option-label"><input type="radio" name="q3" value="C">(গ) হিমপ্রাচীর</label>
                    <label class="option-label"><input type="radio" name="q3" value="D">(ঘ) হিমগুল্ম</label>
                </div>
                <div class="explanation-box" id="exp-3">
                    <strong>সঠিক উত্তর: (গ) হিমপ্রাচীর</strong><br>
                    ব্যাখ্যা: সমুদ্রের যেখানে উষ্ণ ও শীতল স্রোত মিলিত হয়, সেখানে দুই স্রোতের জলের রং ও ঘনত্বের পার্থক্যের জন্য একটি স্পষ্ট সীমারেখা বা প্রাচীরের মতো অংশ দেখা যায়। একেই হিমপ্রাচীর বলে।
                </div>
            </div>

            <div class="question-card" data-qnum="4">
                <p class="question-text">৪. ল্যান্ডফিল বা ভরাটকরণ থেকে উৎপন্ন গ্যাসটি হল-</p>
                <div class="options-container">
                    <label class="option-label"><input type="radio" name="q4" value="A">(ক) অক্সিজেন</label>
                    <label class="option-label"><input type="radio" name="q4" value="B">(খ) কার্বন মনোঅক্সাইড</label>
                    <label class="option-label"><input type="radio" name="q4" value="C">(গ) অ্যামোনিয়া</label>
                    <label class="option-label"><input type="radio" name="q4" value="D">(ঘ) মিথেন</label>
                </div>
                <div class="explanation-box" id="exp-4">
                    <strong>সঠিক উত্তর: (ঘ) মিথেন</strong><br>
                    ব্যাখ্যা: বর্জ্য ভরাটকরণ বা ল্যান্ডফিল পদ্ধতিতে নিচু জমিতে জমা করা জৈব বর্জ্যগুলি মাটির নীচে অবায়বীয় ব্যাকটেরিয়া দ্বারা পচে গিয়ে প্রধানত মিথেন গ্যাস উৎপন্ন করে।
                </div>
            </div>

            <div class="question-card" data-qnum="5">
                <p class="question-text">৫. ভারতের 'সিলিকন ভ্যালি' বলা হয়-</p>
                <div class="options-container">
                    <label class="option-label"><input type="radio" name="q5" value="A">(ক) কলকাতা</label>
                    <label class="option-label"><input type="radio" name="q5" value="B">(খ) মুম্বাই</label>
                    <label class="option-label"><input type="radio" name="q5" value="C">(গ) বেঙ্গালুরু</label>
                    <label class="option-label"><input type="radio" name="q5" value="D">(ঘ) delhi</label>
                </div>
                <div class="explanation-box" id="exp-5">
                    <strong>সঠিক উত্তর: (গ) বেঙ্গালুরু</strong><br>
                    ব্যাখ্যা: মার্কিন যুক্তরাষ্ট্রের ক্যালিফোর্নিয়ার সিলিকন ভ্যালির মতো ভারতের কর্ণাটক রাজ্যের বেঙ্গালুরু শহরে সিলিকন ভিত্তিক তথ্যপ্রযুক্তি শিল্পের সর্বাধিক বিকাশ ঘটেছে।
                </div>
            </div>

            <div class="question-card" data-qnum="6">
                <p class="question-text">৬. ভারতের দীর্ঘতম সেচখাল কোনটি?</p>
                <div class="options-container">
                    <label class="option-label"><input type="radio" name="q6" value="A">(ক) উচ্চ গঙ্গা খাল</label>
                    <label class="option-label"><input type="radio" name="q6" value="B">(খ) সিরহিন্দ খাল</label>
                    <label class="option-label"><input type="radio" name="q6" value="C">(গ) |ন্দিরা গান্ধী খাল</label>
                    <label class="option-label"><input type="radio" name="q6" value="D">(ঘ) দামোদর খাল</label>
                </div>
                <div class="explanation-box" id="exp-6">
                    <strong>সঠিক উত্তর: (গ) ইন্দিরা গান্ধী খাল</strong><br>
                    ব্যাখ্যা: রাজস্থানের ইন্দিরা গান্ধী খাল (যার দৈর্ঘ্য প্রায় ৫৮২ কিমি) হলো ভারতের দীর্ঘতম সেচখাল।
                </div>
            </div>

            <div class="question-card" data-qnum="7">
                <p class="question-text">৭. দক্ষিণ ভারতের সর্বোচ্চ পর্বতশৃঙ্গ হলো-</p>
                <div class="options-container">
                    <label class="option-label"><input type="radio" name="q7" value="A">(ক) দোদাবেতা</label>
                    <label class="option-label"><input type="radio" name="q7" value="B">(খ) অমরকণ্টক</label>
                    <label class="option-label"><input type="radio" name="q7" value="C">(গ) আনাইমুদি</label>
                    <label class="option-label"><input type="radio" name="q7" value="D">(ঘ) মহেন্দ্রগিরি</label>
                </div>
                <div class="explanation-box" id="exp-7">
                    <strong>সঠিক উত্তর: (গ) আনাইমুদি</strong><br>
                    ব্যাখ্যা: আনাইমুদি (২৬৯০ মিটার) আন্নামালাই পর্বতে অবস্থিত, যা সমগ্র দক্ষিণ ভারতের সর্বোচ্চ শৃঙ্গ।
                </div>
            </div>

            <div class="question-card" data-qnum="8">
                <p class="question-text">৮. উপগ্রহ চিত্রে গভীর বনভূমি বা উদ্ভিদ বোঝাতে কোন ছদ্ম রং (False Colour) ব্যবহার করা হয়?</p>
                <div class="options-container">
                    <label class="option-label"><input type="radio" name="q8" value="A">(ক) সবুজ</label>
                    <label class="option-label"><input type="radio" name="q8" value="B">(খ) লাল বা গাঢ় লাল</label>
                    <label class="option-label"><input type="radio" name="q8" value="C">(গ) গাঢ় নীল</label>
                    <label class="option-label"><input type="radio" name="q8" value="D">(ঘ) হলুদ</label>
                </div>
                <div class="explanation-box" id="exp-8">
                    <strong>সঠিক উত্তর: (খ) লাল বা গাঢ় লাল</strong><br>
                    ব্যাখ্যা: উপগ্রহ চিত্রে সেন্সরে ইনফ্রারেড রশ্মির প্রতিফলনের কারণে সবুজ উদ্ভিদ বা গভীর অরণ্যকে লাল বা গাঢ় লাল রঙে দেখানো হয়।
                </div>
            </div>

            <div class="question-card" data-qnum="9">
                <p class="question-text">৯. মরা কোটাল বা মরা জোয়ার কোন তিথিতে সৃষ্টি হয়?</p>
                <div class="options-container">
                    <label class="option-label"><input type="radio" name="q9" value="A">(ক) পূর্ণিমা</label>
                    <label class="option-label"><input type="radio" name="q9" value="B">(খ) অমাবস্যা</label>
                    <label class="option-label"><input type="radio" name="q9" value="C">(গ) শুক্ল ও কৃষ্ণপক্ষের অষ্টমী</label>
                    <label class="option-label"><input type="radio" name="q9" value="D">(ঘ) একাদশী</label>
                </div>
                <div class="explanation-box" id="exp-9">
                    <strong>সঠিক উত্তর: (গ) শুক্ল ও কৃষ্ণপক্ষের অষ্টমী</strong><br>
                    ব্যাখ্যা: শুক্ল ও কৃষ্ণপক্ষের অষ্টমী তিথিতে চাঁদ ও সূর্য পৃথিবীর সাপেক্ষে সমকোণে অবস্থান করে। এর ফলে সমুদ্রের জলস্ফীতি অনেক কম হয়, যাকে মরা কোটাল বলে।
                </div>
            </div>

            <div class="question-card" data-qnum="10">
                <p class="question-text">১০. ভারতের মহাকাশ গবেষণা সংস্থা (ISRO)-এর সদর দপ্তর কোথায় অবস্থিত?</p>
                <div class="options-container">
                    <label class="option-label"><input type="radio" name="q10" value="A">(ক) দিল্লি</label>
                    <label class="option-label"><input type="radio" name="q10" value="B">(খ) চেন্নাই</label>
                    <label class="option-label"><input type="radio" name="q10" value="C">(গ) বেঙ্গালুরু</label>
                    <label class="option-label"><input type="radio" name="q10" value="D">(ঘ) কলকাতা</label>
                </div>
                <div class="explanation-box" id="exp-10">
                    <strong>সঠিক উত্তর: (গ) বেঙ্গালুরু</strong><br>
                    ব্যাখ্যা: ভারতের মহাকাশ গবেষণা সংস্থা ISRO-এর প্রধান কার্যালয় বা সদর দপ্তর কর্ণাটকের বেঙ্গালুরু শহরে অবস্থিত।
                </div>
            </div>

            <div style="text-align: center; margin-top: 25px; margin-bottom: 20px;">
                <button type="button" id="submit-btn" class="btn" style="background-color: #34a853;" onclick="submitExam()">খাতা জমা দিন (Submit)</button>
            </div>
        </form>
    </div>
</div>

<script>
    // 🔒 সিকিউরড অ্যানসার কি (কোডের ভেতরে উত্তর লুকিয়ে রাখা হলো)
    const secureAnswers = {
        q1: "A", q2: "C", q3: "C", q4: "D", q5: "C",
        q6: "C", q7: "C", q8: "B", q9: "C", q10: "C"
    };

    let totalTime = 600; // ১০ মিনিট
    let timerInterval;

    function startExam() {
        const nameInput = document.getElementById('student-name-input').value.trim();
        if (nameInput === "") {
            alert("দয়া করে পরীক্ষা শুরু করার আগে আপনার নাম লিখুন!");
            return;
        }

        document.getElementById('start-screen').style.display = 'none';
        document.getElementById('exam-screen').style.display = 'block';
        document.getElementById('display-student-name').innerText = nameInput;

        timerInterval = setInterval(updateTimer, 1000);
    }

    function updateTimer() {
        let minutes = Math.floor(totalTime / 60);
        let seconds = totalTime % 60;

        seconds = seconds < 10 ? '0' + seconds : seconds;
        minutes = minutes < 10 ? '0' + minutes : minutes;

        document.getElementById('timer').innerText = minutes + ":" + seconds;

        if (totalTime <= 0) {
            clearInterval(timerInterval);
            alert("সময় শেষ! আপনার উত্তরপত্রটি স্বয়ংক্রিয়ভাবে জমা নেওয়া হলো।");
            submitExam();
        }
        totalTime--;
    }

    function submitExam() {
        clearInterval(timerInterval);
        document.getElementById('submit-btn').style.display = 'none';
        document.getElementById('timer').innerText = "00:00 (জমা দেওয়া হয়েছে)";

        const form = document.getElementById('quiz-form');
        let totalScore = 0;

        const cards = document.getElementsByClassName('question-card');
        
        for (let card of cards) {
            const qNum = card.getAttribute('data-qnum');
            const radioButtons = form.elements['q' + qNum];
            const labels = card.getElementsByClassName('option-label');
            const correctAnswer = secureAnswers['q' + qNum];
            
            let studentAnswer = "";

            for (let i = 0; i < radioButtons.length; i++) {
                radioButtons[i].disabled = true; // বাটন লক করা
                
                if (radioButtons[i].checked) {
                    studentAnswer = radioButtons[i].value;
                }

                // জাভাস্ক্রিপ্ট সিকিউরড উত্তর মিলিয়ে এখানে সঠিক অপশনটিকে সবুজ করবে
                if (radioButtons[i].value === correctAnswer) {
                    labels[i].classList.add('correct');
                }
                
                // ছাত্র ভুল দিয়ে থাকলে সেটা লাল হবে
                if (radioButtons[i].checked && radioButtons[i].value !== correctAnswer) {
                    labels[i].classList.add('wrong');
                }
            }

            if (studentAnswer === correctAnswer) {
                totalScore++;
            }

            document.getElementById('exp-' + qNum).style.display = 'block';
        }

        document.getElementById('res-name').innerText = document.getElementById('student-name-input').value;
        document.getElementById('score').innerText = totalScore;
        document.getElementById('result-box').style.display = 'block';

        window.scrollTo({top: 0, behavior: 'smooth'});
    }
</script>

</body>
</html>


    <div id="exam-screen" style="display: none;">
        <div class="exam-header">
            <div>পরীক্ষার্থী: <span id="display-student-name" style="color: #1a73e8;"></span></div>
            <div class="timer-box">সময় বাকি: <span id="timer">10:00</span></div>
        </div>

        <div id="result-box" class="result-box">
            <h2>🎉 পরীক্ষার ফলাফল 🎉</h2>
            <p style="font-size: 18px;">পরীক্ষার্থী: <span id="res-name" style="font-weight: bold;"></span></p>
            <p style="font-size: 24px; font-weight: bold;">মোট স্কোর: <span id="score">0</span> / ১০</p>
            <p style="font-size: 16px; color: #5f6368;">নিচে আপনার উত্তরপত্র পর্যালোচনা করুন।</p>
        </div>

        <form id="quiz-form">
            <div class="question-card" data-qnum="1">
                <p class="question-text">১. ভারতের 'জাতীয় মহাফেজখানা' (National Archives of India) কোথায় অবস্থিত?</p>
                <div class="options-container">
                    <label class="option-label"><input type="radio" name="q1" value="wrong">(ক) কলকাতা</label>
                    <label class="option-label"><input type="radio" name="q1" value="correct">(খ) নতুন দিল্লি</label>
                    <label class="option-label"><input type="radio" name="q1" value="wrong">(গ) মুম্বাই</label>
                    <label class="option-label"><input type="radio" name="q1" value="wrong">(ঘ) চেন্নাই</label>
                </div>
                <div class="explanation-box" id="exp-1">
                    <strong>সঠিক উত্তর: (খ) নতুন দিল্লি</strong><br>
                    ব্যাখ্যা: ভারতের জাতীয় মহাফেজখানা বা ন্যাশনাল আর্কাইভস অফ ইন্ডিয়া নতুন দিল্লিতে অবস্থিত। এখানে সরকারি নথিপত্র ও ঐতিহাসিক দলিল সংরক্ষিত থাকে। এটি নতুন ইতিহাস চর্চার অন্যতম প্রধান উপাদান।
                </div>
            </div>

            <div class="question-card" data-qnum="2">
                <p class="question-text">২. 'বামাবোধিনী' পত্রিকার সম্পাদক কে ছিলেন?</p>
                <div class="options-container">
                    <label class="option-label"><input type="radio" name="q2" value="correct">(ক) উমেশচন্দ্র দত্ত</label>
                    <label class="option-label"><input type="radio" name="q2" value="wrong">(খ) হরিশচন্দ্র মুখোপাধ্যায়</label>
                    <label class="option-label"><input type="radio" name="q2" value="wrong">(গ) দেবেন্দ্রনাথ ঠাকুর</label>
                    <label class="option-label"><input type="radio" name="q2" value="wrong">(ঘ) ঈশ্বরচন্দ্র বিদ্যাসাগর</label>
                </div>
                <div class="explanation-box" id="exp-2">
                    <strong>সঠিক উত্তর: (ক) উমেশচন্দ্র দত্ত</strong><br>
                    ব্যাখ্যা: ১৮৬৩ খ্রিস্টাব্দে উমেশচন্দ্র দত্তের সম্পাদনায় 'বামাবোধিনী' পত্রিকা প্রকাশিত হয়। এটি ছিল তৎকালীন বাঙালি সমাজের নারীদের বা বামাকুলের চেতনা ও শিক্ষার প্রসারের জন্য একটি অত্যন্ত গুরুত্বপূর্ণ পত্রিকা।
                </div>
            </div>

            <div class="question-card" data-qnum="3">
                <p class="question-text">৩. কলকাতা মেডিকেল কলেজ কত খ্রিস্টাব্দে প্রতিষ্ঠিত হয়েছিল?</p>
                <div class="options-container">
                    <label class="option-label"><input type="radio" name="q3" value="wrong">(ক) ১৮১৭ খ্রিস্টাব্দে</label>
                    <label class="option-label"><input type="radio" name="q3" value="wrong">(খ) ১৮২৩ খ্রিস্টাব্দে</label>
                    <label class="option-label"><input type="radio" name="q3" value="correct">(গ) ১৮৩৫ খ্রিস্টাব্দে</label>
                    <label class="option-label"><input type="radio" name="q3" value="wrong">(ঘ) ১৮৫৭ খ্রিস্টাব্দে</label>
                </div>
                <div class="explanation-box" id="exp-3">
                    <strong>সঠিক উত্তর: (গ) ১৮৩৫ খ্রিস্টাব্দে</strong><br>
                    ব্যাখ্যা: লর্ড উইলিয়াম বেন্টিঙ্কের উদ্যোগে ১৮৩৫ খ্রিস্টাব্দে কলকাতা মেডিকেল কলেজ প্রতিষ্ঠিত হয়। এটি এশিয়ায় পাশ্চাত্য চিকিৎসা শিক্ষার ক্ষেত্রে একটি যুগান্তকারী পদক্ষেপ ছিল।
                </div>
            </div>

            <div class="question-card" data-qnum="4">
                <p class="question-text">৪. উলগুলান (Ulgulan) বলতে কোন্ বিদ্রোহকে বোঝায়?</p>
                <div class="options-container">
                    <label class="option-label"><input type="radio" name="q4" value="wrong">(ক) সাঁওতাল বিদ্রোহ</label>
                    <label class="option-label"><input type="radio" name="q4" value="correct">(খ) মুণ্ডা বিদ্রোহ</label>
                    <label class="option-label"><input type="radio" name="q4" value="wrong">(গ) কোল বিদ্রোহ</label>
                    <label class="option-label"><input type="radio" name="q4" value="wrong">(ঘ) চুয়াড় বিদ্রোহ</label>
                </div>
                <div class="explanation-box" id="exp-4">
                    <strong>সঠিক উত্তর: (খ) মুণ্ডা বিদ্রোহ</strong><br>
                    \ব্যাখ্যা: বিরসা মুণ্ডার নেতৃত্বে ১৮৯৯-১৯০০ খ্রিস্টাব্দে সংঘটিত মুণ্ডা বিদ্রোহকে 'উলগুলান' বলা হয়। উলগুলান শব্দের অর্থ হলো 'প্রবল আলোড়ন' বা 'মহা গোলযোগ'।
                </div>
            </div>

            <div class="question-card" data-qnum="5">
                <p class="question-text">৫. ১৮৫৭ খ্রিস্টাব্দের মহাবিদ্রোহের সময় ভারতের গভর্নর জেনারেল কে ছিলেন?</p>
                <div class="options-container">
                    <label class="option-label"><input type="radio" name="q5" value="wrong">(ক) লর্ড ডালহৌসি</label>
                    <label class="option-label"><input type="radio" name="q5" value="correct">(খ) লর্ড ক্যানিং</label>
                    <label class="option-label"><input type="radio" name="q5" value="wrong">(গ) লর্ড উইলিয়াম বেন্টিঙ্ক</label>
                    <label class="option-label"><input type="radio" name="q5" value="wrong">(ঘ) লর্ড কার্জন</label>
                </div>
                <div class="explanation-box" id="exp-5">
                    <strong>সঠিক উত্তর: (খ) লর্ড ক্যানিং</strong><br>
                    ব্যাখ্যা: ১৮NT৭ খ্রিস্টাব্দের সিপাহি বিদ্রোহ বা মহাবিদ্রোহের সময় লর্ড ক্যানিং ভারতের গভর্নর জেনারেল ছিলেন। বিদ্রোহের পর ১৮৫৮ খ্রিস্টাব্দের রানি ভিক্টোরিয়ার ঘোষণার দ্বারা তিনি ভারতের প্রথম 'ভাইসরয়' নিযুক্ত হন।
                </div>
            </div>

            <div class="question-card" data-qnum="6">
                <p class="question-text">৬. 'বন্দে মাতরম্' সঙ্গীতটি কোন্ উপন্যাসের অন্তর্গত?</p>
                <div class="options-container">
                    <label class="option-label"><input type="radio" name="q6" value="wrong">(ক) গোরা</label>
                    <label class="option-label"><input type="radio" name="q6" value="wrong">(খ) পথের দাবী</label>
                    <label class="option-label"><input type="radio" name="q6" value="correct">(গ) আনন্দমঠ</label>
                    <label class="option-label"><input type="radio" name="q6" value="wrong">(ঘ) বর্তমান ভারত</label>
                </div>
                <div class="explanation-box" id="exp-6">
                    <strong>সঠিক উত্তর: (গ) আনন্দমঠ</strong><br>
                    ব্যাখ্যা: বঙ্কিমচন্দ্র চট্টোপাধ্যায়ের বিখ্যাত রাজনৈতিক উপন্যাস 'आनন্দমঠ' (১৮৮২ খ্রি.) থেকে 'বন্দে মাতরম্' সঙ্গীতটি নেওয়া হয়েছে। এই গানটি ভারতীয় জাতীয়তাবাদের বিকাশে প্রধান উদ্দীপক হিসেবে কাজ করেছিল।
                </div>
            </div>

            <div class="question-card" data-qnum="7">
                <p class="question-text">৭. ভারতে প্রথম ছাপাখানা কারা প্রতিষ্ঠা করেছিল?</p>
                <div class="options-container">
                    <label class="option-label"><input type="radio" name="q7" value="correct">(ক) পর্তুগিজরা</label>
                    <label class="option-label"><input type="radio" name="q7" value="wrong">(খ) ইংরেজরা</label>
                    <label class="option-label"><input type="radio" name="q7" value="wrong">(গ) ওলন্দাজরা</label>
                    <label class="option-label"><input type="radio" name="q7" value="wrong">(ঘ) ফরাসিরা</label>
                </div>
                <div class="explanation-box" id="exp-7">
                    <strong>সঠিক উত্তর: (ক) পর্তুগিজরা</strong><br>
                    ব্যাখ্যা: ১৫৫৬ খ্রিস্টাব্দে পর্তুগিজরা ভারতের গোয়াতে প্রথম ছাপাখানা বা প্রিন্টিং প্রেস স্থাপন করে। বাংলায় প্রথম ছাপাখানা হুগলিতে ইংরেজদের উদ্যোগে স্থাপিত হয়েছিল।
                </div>
            </div>

            <div class="question-card" data-qnum="8">
                <p class="question-text">৮. 'একা আন্দোলন' বা একতা আন্দোলনের নেতা কে ছিলেন?</p>
                <div class="options-container">
                    <label class="option-label"><input type="radio" name="q8" value="wrong">(ক) বাবা রামচন্দ্র</label>
                    <label class="option-label"><input type="radio" name="q8" value="correct">(খ) মাদারি পাসি</label>
                    <label class="option-label"><input type="radio" name="q8" value="wrong">(গ) অল্লুরি সিতারাম রাজু</label>
                    <label class="option-label"><input type="radio" name="q8" value="wrong">(ঘ) বল্লভভাই প্যাটেল</label>
                </div>
                <div class="explanation-box" id="exp-8">
                    <strong>সঠিক উত্তর: (খ) মাদারি পাসি</strong><br>
                    ব্যাখ্যা: ১৯২১-২২ খ্রিস্টাব্দে উত্তরপ্রদেশের হরদোই, বারবাঁকি প্রভৃতি অঞ্চলে অতিরিক্ত খাজনা আদায়ের বিরুদ্ধে 'একা আন্দোলন' গড়ে ওঠে। এই কৃষক আন্দোলনের প্রধান নেতা ছিলেন মাদারি পাসি।
                </div>
            </div>

            <div class="question-card" data-qnum="9">
                <p class="question-text">৯. 'দিপালী সংঘ' কে প্রতিষ্ঠা করেছিলেন?</p>
                <div class="options-container">
                    <label class="option-label"><input type="radio" name="q9" value="wrong">(ক) কল্পনা দত্ত</label>
                    <label class="option-label"><input type="radio" name="q9" value="wrong">(খ) প্রীতিলতা ওয়াদ্দেদার</label>
                    <label class="option-label"><input type="radio" name="q9" value="correct">(গ) লীলা নাগ (রায়)</label>
                    <label class="option-label"><input type="radio" name="q9" value="wrong">(ঘ) বীণা দাস</label>
                </div>
                <div class="explanation-box" id="exp-9">
                    <strong>সঠিক উত্তর: (গ) লীলা নাগ (রায়)</strong><br>
                    ব্যাখ্যা: ১৯২৩ খ্রিস্টাব্দে ঢাকায় লীলা নাগ (পরবর্তীকালে লীলা রায়) 'দিপালী সংঘ' প্রতিষ্ঠা করেন। এটি ছিল নারী শিক্ষার প্রসার ও বিপ্লবীবাদী ভাবধারায় নারীদের আত্মরক্ষার শিক্ষা দেওয়ার একটি অন্যতম প্রধান বিপ্লবী নারী সংগঠন।
                </div>
            </div>

            <div class="question-card" data-qnum="10">
                <p class="question-text">১০. ভারতের স্বাধীনতাকালে কাশ্মীরের মহারাজা কে ছিলেন?</p>
                <div class="options-container">
                    <label class="option-label"><input type="radio" name="q10" value="wrong">(ক) শেখ আবদুল্লা</label>
                    <label class="option-label"><input type="radio" name="q10" value="correct">(খ) হরি সিং</label>
                    <label class="option-label"><input type="radio" name="q10" value="wrong">(গ) করণ সিং</label>
                    <label class="option-label"><input type="radio" name="q10" value="wrong">(ঘ) গুলাব সিং</label>
                </div>
                <div class="explanation-box" id="exp-10">
                    <strong>সঠিক উত্তর: (খ) হরি সিং</strong><br>
                    ব্যাখ্যা: ১৯৪৭ খ্রিস্টাব্দে ভারতের স্বাধীনতাপ্রাপ্তি ও দেশভাগের সময় কাশ্মীরের মহারাজা ছিলেন হরি সিং। পরবর্তীকালে পাকিস্তানি হানাদারদের আক্রমণের মুখে তিনি ভারতের সাথে 'ভারতভুক্তি দলিল'-এ স্বাক্ষর করেন।
                </div>
            </div>

            <div style="text-align: center; margin-top: 30px; margin-bottom: 5px;">
                <button type="button" id="submit-btn" class="btn" style="background-color: #34a853;" onclick="submitExam()">খাতা জমা দিন (Submit)</button>
            </div>
        </form>
    </div>
</div>

<script>
    let totalTime = 600; // ১০ মিনিট সেকেন্ডে
    let timerInterval;

    function startExam() {
        const nameInput = document.getElementById('student-name-input').value.trim();
        if (nameInput === "") {
            alert("দয়া করে পরীক্ষা শুরু করার আগে আপনার নাম লিখুন!");
            return;
        }

        document.getElementById('start-screen').style.display = 'none';
        document.getElementById('exam-screen').style.display = 'block';
        document.getElementById('display-student-name').innerText = nameInput;

        timerInterval = setInterval(updateTimer, 1000);
    }

    function updateTimer() {
        let minutes = Math.floor(totalTime / 60);
        let seconds = totalTime % 60;

        seconds = seconds < 10 ? '0' + seconds : seconds;
        minutes = minutes < 10 ? '0' + minutes : minutes;

        document.getElementById('timer').innerText = minutes + ":" + seconds;

        if (totalTime <= 0) {
            clearInterval(timerInterval);
            alert("সময় শেষ! আপনার উত্তরপত্রটি স্বয়ংক্রিয়ভাবে জমা নেওয়া হলো।");
            submitExam();
        }
        totalTime--;
    }

    function submitExam() {
        clearInterval(timerInterval);
        document.getElementById('submit-btn').style.display = 'none';
        document.getElementById('timer').innerText = "00:00 (জমা দেওয়া হয়েছে)";

        const form = document.getElementById('quiz-form');
        let totalScore = 0;

        const cards = document.getElementsByClassName('question-card');
        
        for (let card of cards) {
            const qNum = card.getAttribute('data-qnum');
            const radioButtons = form.elements['q' + qNum];
            const labels = card.getElementsByClassName('option-label');
            
            let selectedValue = "";

            for (let i = 0; i < radioButtons.length; i++) {
                radioButtons[i].disabled = true;
                
                if (radioButtons[i].checked) {
                    selectedValue = radioButtons[i].value;
                }

                if (radioButtons[i].value === "correct") {
                    labels[i].classList.add('correct');
                }
                
                if (radioButtons[i].checked && radioButtons[i].value === "wrong") {
                    labels[i].classList.add('wrong');
                }
            }

            if (selectedValue === "correct") {
                totalScore++;
            }

            document.getElementById('exp-' + qNum).style.display = 'block';
        }

        document.getElementById('res-name').innerText = document.getElementById('student-name-input').value;
        document.getElementById('score').innerText = totalScore;
        document.getElementById('result-box').style.display = 'block';

        window.scrollTo({top: 0, behavior: 'smooth'});
    }
</script>

</body>
</html>

        <br>
        <button class="btn" onclick="startExam()">পরীক্ষা শুরু করো</button>
    </div>

    <div id="exam-screen" style="display: none;">
        <div class="exam-header">
            <div>পরীক্ষার্থী: <span id="display-student-name" style="color: #1a73e8;"></span></div>
            <div class="timer-box">সময় বাকি: <span id="timer">10:00</span></div>
        </div>

        <div id="result-box" class="result-box">
            <h2>🎉 পরীক্ষার ফলাফল 🎉</h2>
            <p style="font-size: 18px;">পরীক্ষার্থী: <span id="res-name" style="font-weight: bold;"></span></p>
            <p style="font-size: 24px; font-weight: bold;">মোট স্কোর: <span id="score">0</span> / ১০</p>
            <p style="font-size: 16px; color: #5f6368;">নিচে আপনার উত্তরপত্র পর্যালোচনা করুন।</p>
        </div>

        <form id="quiz-form">
            <div class="question-card" data-qnum="1">
                <p class="question-text">১. পাখির पैरों মতো বদ্বীপ দেখা যায় যে নদীর মোহանায়-</p>
                <div class="options-container">
                    <label class="option-label"><input type="radio" name="q1" value="correct">(ক) মিসিসিপি-মিসৌরি</label>
                    <label class="option-label"><input type="radio" name="q1" value="wrong">(খ) হোয়াংহো</label>
                    <label class="option-label"><input type="radio" name="q1" value="wrong">(গ) ইরাবতী</label>
                    <label class="option-label"><input type="radio" name="q1" value="wrong">(ঘ) তাইবার</label>
                </div>
                <div class="explanation-box" id="exp-1">
                    <strong>সঠিক উত্তর: (ক) মিসিসিপি-মিসৌরি</strong><br>
                    ব্যাখ্যা: মিসিসিপি-মিসৌরি নদীর মোহানায় নদীস্রোত ও সমুদ্রস্রোতের পারস্পরিক প্রভাবে পলি সঞ্চিত হয়ে ঠিক পাখির পায়ের মতো দেখতে একটি বদ্বীপ গঠিত হয়েছে।
                </div>
            </div>

            <div class="question-card" data-qnum="2">
                <p class="question-text">২. বায়ুমণ্ডলের যে স্তরে আবহাওয়ার গোলযোগ দেখা যায় সেই স্তরটি হলো-</p>
                <div class="options-container">
                    <label class="option-label"><input type="radio" name="q2" value="wrong">(ক) স্ট্র্যাটোস্ফিয়ার</label>
                    <label class="option-label"><input type="radio" name="q2" value="wrong">(খ) মেসোস্ফিয়ার</label>
                    <label class="option-label"><input type="radio" name="q2" value="correct">(গ) トロポস্ফিয়ার</label>
                    <label class="option-label"><input type="radio" name="q2" value="wrong">(ঘ) আয়নোস্ফিয়ার</label>
                </div>
                <div class="explanation-box" id="exp-2">
                    <strong>সঠিক উত্তর: (গ) ট্রপোস্ফিয়ার</strong><br>
                    ব্যাখ্যা: ট্রপোস্ফিয়ার হলো বায়ুমণ্ডলের সবচেয়ে নীচের স্তর। ধূলিকণা ও জলীয় বাষ্পের প্রায় পুরোটাই এই স্তরে থাকায় মেঘ, ঝড়, বৃষ্টি, বজ্রপাত ইত্যাদি যাবতীয় আবহাওয়াগত গোলযোগ বা অশান্ত অবস্থা এই স্তরেই ঘটে। এই কারণে একে 'ক্ষুব্ধমণ্ডল' বলা হয়।
                </div>
            </div>

            <div class="question-card" data-qnum="3">
                <p class="question-text">৩. সমুদ্রের যে স্থানে উষ্ণ ও শীতল স্রোত উভয়ে মিলিত হয় তাকে বলে-</p>
                <div class="options-container">
                    <label class="option-label"><input type="radio" name="q3" value="wrong">(ক) হিমানী সম্প্রপাত</label>
                    <label class="option-label"><input type="radio" name="q3" value="wrong">(খ) হিমশৈল</label>
                    <label class="option-label"><input type="radio" name="q3" value="correct">(গ) হিমপ্রাচীর</label>
                    <label class="option-label"><input type="radio" name="q3" value="wrong">(ঘ) হিমগুল্ম</label>
                </div>
                <div class="explanation-box" id="exp-3">
                    <strong>সঠিক উত্তর: (গ) হিমপ্রাচীর</strong><br>
                    ব্যাখ্যা: সমুদ্রের যেখানে উষ্ণ ও শীতল স্রোত মিলিত হয়, সেখানে দুই স্রোতের জলের রং ও ঘনত্বের পার্থক্যের জন্য একটি স্পষ্ট সীমারেখা বা প্রাচীরের মতো অংশ দেখা যায়। একেই হিমপ্রাচীর বলে।
                </div>
            </div>

            <div class="question-card" data-qnum="4">
                <p class="question-text">৪. ল্যান্ডফিল বা ভরাটকরণ থেকে উৎপন্ন গ্যাসটি হল-</p>
                <div class="options-container">
                    <label class="option-label"><input type="radio" name="q4" value="wrong">(ক) অক্সিজেন</label>
                    <label class="option-label"><input type="radio" name="q4" value="wrong">(খ) কার্বন মনোঅক্সাইড</label>
                    <label class="option-label"><input type="radio" name="q4" value="wrong">(গ) অ্যামোনিয়া</label>
                    <label class="option-label"><input type="radio" name="q4" value="correct">(ঘ) মিথেন</label>
                </div>
                <div class="explanation-box" id="exp-4">
                    <strong>সঠিক উত্তর: (ঘ) মিথেন</strong><br>
                    ব্যাখ্যা: বর্জ্য ভরাটকরণ বা ল্যান্ডফিল পদ্ধতিতে নিচু জমিতে জমা করা জৈব বর্জ্যগুলি মাটির নীচে অবায়বীয় ব্যাকটেরিয়া দ্বারা পচে গিয়ে প্রধানত মিথেন গ্যাস উৎপন্ন করে।
                </div>
            </div>

            <div class="question-card" data-qnum="5">
                <p class="question-text">৫. ভারতের 'সিলিকন ভ্যালি' বলা হয়-</p>
                <div class="options-container">
                    <label class="option-label"><input type="radio" name="q5" value="wrong">(ক) কলকাতা</label>
                    <label class="option-label"><input type="radio" name="q5" value="wrong">(খ) মুম্বাই</label>
                    <label class="option-label"><input type="radio" name="q5" value="correct">(গ) বেঙ্গালুরু</label>
                    <label class="option-label"><input type="radio" name="q5" value="wrong">(ঘ) দিল্লি</label>
                </div>
                <div class="explanation-box" id="exp-5">
                    <strong>সঠিক উত্তর: (গ) বেঙ্গালুরু</strong><br>
                    ব্যাখ্যা: মার্কিন যুক্তরাষ্ট্রের ক্যালিফোর্নিয়ার সিলিকন ভ্যালির মতো ভারতের কর্ণাটক রাজ্যের বেঙ্গালুরু শহরে সিলিকন ভিত্তিক তথ্যপ্রযুক্তি শিল্পের সর্বাধিক বিকাশ ঘটেছে।
                </div>
            </div>

            <div class="question-card" data-qnum="6">
                <p class="question-text">৬. ভারতের দীর্ঘতম সেচখাল কোনটি?</p>
                <div class="options-container">
                    <label class="option-label"><input type="radio" name="q6" value="wrong">(ক) উচ্চ গঙ্গা খাল</label>
                    <label class="option-label"><input type="radio" name="q6" value="wrong">(খ) সিরহিন্দ খাল</label>
                    <label class="option-label"><input type="radio" name="q6" value="correct">(গ) ইন্দিরা গান্ধী খাল</label>
                    <label class="option-label"><input type="radio" name="q6" value="wrong">(ঘ) দামোদর খাল</label>
                </div>
                <div class="explanation-box" id="exp-6">
                    <strong>সঠিক উত্তর: (গ) ইন্দিরা গান্ধী খাল</strong><br>
                    ব্যাখ্যা: রাজস্থানের ইন্দিরা গান্ধী খাল (যার দৈর্ঘ্য প্রায় ৫৮২ কিমি) হলো ভারতের দীর্ঘতম সেচখাল।
                </div>
            </div>

            <div class="question-card" data-qnum="7">
                <p class="question-text">৭. দক্ষিণ ভারতের সর্বোচ্চ পর্বতশৃঙ্গ হলো-</p>
                <div class="options-container">
                    <label class="option-label"><input type="radio" name="q7" value="wrong">(ক) দোদাবেতা</label>
                    <label class="option-label"><input type="radio" name="q7" value="wrong">(খ) অমরকণ্টক</label>
                    <label class="option-label"><input type="radio" name="q7" value="correct">(গ) আনাইমুদি</label>
                    <label class="option-label"><input type="radio" name="q7" value="wrong">(ঘ) মহেন্দ্রগিরি</label>
                </div>
                <div class="explanation-box" id="exp-7">
                    <strong>সঠিক উত্তর: (গ) আনাইমুদি</strong><br>
                    ব্যাখ্যা: আনাইমুদি (২৬৯০ মিটার) আন্নামালাই পর্বতে অবস্থিত, যা সমগ্র দক্ষিণ ভারতের সর্বোচ্চ শৃঙ্গ।
                </div>
            </div>

            <div class="question-card" data-qnum="8">
                <p class="question-text">৮. উপগ্রহ চিত্রে গভীর বনভূমি বা উদ্ভিদ বোঝাতে কোন ছদ্ম রং (False Colour) ব্যবহার করা হয়?</p>
                <div class="options-container">
                    <label class="option-label"><input type="radio" name="q8" value="wrong">(ক) সবুজ</label>
                    <label class="option-label"><input type="radio" name="q8" value="correct">(খ) লাল বা গাঢ় লাল</label>
                    <label class="option-label"><input type="radio" name="q8" value="wrong">(গ) গাঢ় নীল</label>
                    <label class="option-label"><input type="radio" name="q8" value="wrong">(ঘ) হলুদ</label>
                </div>
                <div class="explanation-box" id="exp-8">
                    <strong>সঠিক উত্তর: (খ) লাল বা গাঢ় লাল</strong><br>
                    ব্যাখ্যা: উপগ্রহ চিত্রে সেন্সরে ইনফ্রারেড রশ্মির প্রতিফলনের কারণে সবুজ উদ্ভিদ বা গভীর অরণ্যকে লাল বা গাঢ় লাল রঙে দেখানো হয়।
                </div>
            </div>

            <div class="question-card" data-qnum="9">
                <p class="question-text">৯. মরা কোটাল বা মরা জোয়ার কোন তিথিতে সৃষ্টি হয়?</p>
                <div class="options-container">
                    <label class="option-label"><input type="radio" name="q9" value="wrong">(ক) পূর্ণিমা</label>
                    <label class="option-label"><input type="radio" name="q9" value="wrong">(খ) অমাবস্যা</label>
                    <label class="option-label"><input type="radio" name="q9" value="correct">(গ) শুক্ল ও কৃষ্ণপক্ষের অষ্টমী</label>
                    <label class="option-label"><input type="radio" name="q9" value="wrong">(ঘ) একাদশী</label>
                </div>
                <div class="explanation-box" id="exp-9">
                    <strong>সঠিক উত্তর: (গ) শুক্ল ও কৃষ্ণপক্ষের অষ্টমী</strong><br>
                    ব্যাখ্যা: শুক্ল ও কৃষ্ণপক্ষের অষ্টমী তিথিতে চাঁদ ও সূর্য পৃথিবীর সাপেক্ষে সমকোণে অবস্থান করে। এর ফলে সমুদ্রের জলস্ফীতি অনেক কম হয়, যাকে মরা কোটাল বলে।
                </div>
            </div>

            <div class="question-card" data-qnum="10">
                <p class="question-text">১০. ভারতের মহাকাশ গবেষণা সংস্থা (ISRO)-এর সদর দপ্তর কোথায় অবস্থিত?</p>
                <div class="options-container">
                    <label class="option-label"><input type="radio" name="q10" value="wrong">(ক) দিল্লি</label>
                    <label class="option-label"><input type="radio" name="q10" value="wrong">(খ) চেন্নাই</label>
                    <label class="option-label"><input type="radio" name="q10" value="correct">(গ) বেঙ্গালুরু</label>
                    <label class="option-label"><input type="radio" name="q10" value="wrong">(ঘ) কলকাতা</label>
                </div>
                <div class="explanation-box" id="exp-10">
                    <strong>সঠিক উত্তর: (গ) বেঙ্গালুরু</strong><br>
                    ব্যাখ্যা: ভারতের মহাকাশ গবেষণা সংস্থা ISRO-এর প্রধান কার্যালয় বা সদর দপ্তর কর্ণাটকের বেঙ্গালুরু শহরে অবস্থিত।
                </div>
            </div>

            <div style="text-align: center; margin-top: 30px; margin-bottom: 5px;">
                <button type="button" id="submit-btn" class="btn" style="background-color: #34a853;" onclick="submitExam()">খাতা জমা দিন (Submit)</button>
            </div>
        </form>
    </div>
</div>

<script>
    let totalTime = 600; // ১০ মিনিট সেকেন্ডে (10 * 60)
    let timerInterval;

    // পরীক্ষা শুরু করার ফাংশন
    function startExam() {
        const nameInput = document.getElementById('student-name-input').value.trim();
        if (nameInput === "") {
            alert("দয়া করে পরীক্ষা শুরু করার আগে আপনার নাম লিখুন!");
            return;
        }

        // স্ক্রিন অদলবদল
        document.getElementById('start-screen').style.display = 'none';
        document.getElementById('exam-screen').style.display = 'block';
        document.getElementById('display-student-name').innerText = nameInput;

        // টাইমার চালু করা
        timerInterval = setInterval(updateTimer, 1000);
    }

    // টাইমার কাউন্টডাউন ফাংশন
    function updateTimer() {
        let minutes = Math.floor(totalTime / 60);
        let seconds = totalTime % 60;

        seconds = seconds < 10 ? '0' + seconds : seconds;
        minutes = minutes < 10 ? '0' + minutes : minutes;

        document.getElementById('timer').innerText = minutes + ":" + seconds;

        if (totalTime <= 0) {
            clearInterval(timerInterval);
            alert("সময় শেষ! আপনার উত্তরপত্রটি স্বয়ংক্রিয়ভাবে জমা নেওয়া হলো।");
            submitExam(); // টাইম শেষ হলে অটোমেটিক সাবমিট
        }
        totalTime--;
    }

    // পরীক্ষা জমা দেওয়ার মেইন ফাংশন
    function submitExam() {
        clearInterval(timerInterval); // টাইমার স্টপ
        document.getElementById('submit-btn').style.display = 'none'; // সাবমিট বাটন হাইড
        document.getElementById('timer').innerText = "00:00 (জমা দেওয়া হয়েছে)";

        const form = document.getElementById('quiz-form');
        let totalScore = 0;

        // ১ থেকে ১০ পর্যন্ত প্রতিটি কার্ড লুপ করা
        const cards = document.getElementsByClassName('question-card');
        
        for (let card of cards) {
            const qNum = card.getAttribute('data-qnum');
            const radioButtons = form.elements['q' + qNum];
            const labels = card.getElementsByClassName('option-label');
            
            let selectedValue = "";

            // ছাত্র কোন অপশন সিলেক্ট করেছে এবং সঠিক বাটন লক করা
            for (let i = 0; i < radioButtons.length; i++) {
                radioButtons[i].disabled = true; // লক করা হচ্ছে
                
                if (radioButtons[i].checked) {
                    selectedValue = radioButtons[i].value;
                }

                // সঠিক উত্তরের ব্যাকগ্রাউন্ড সবুজ করা
                if (radioButtons[i].value === "correct") {
                    labels[i].classList.add('correct');
                }
                
                // ছাত্র যদি ভুল উত্তর সিলেক্ট করে থাকে তবে লাল করা
                if (radioButtons[i].checked && radioButtons[i].value === "wrong") {
                    labels[i].classList.add('wrong');
                }
            }

            // স্কোর হিসেব করা
            if (selectedValue === "correct") {
                totalScore++;
            }

            // এই প্রশ্নের ব্যাখ্যা বক্সটি ওপেন করা
            document.getElementById('exp-' + qNum).style.display = 'block';
        }

        // রেজাল্ট ড্যাশবোর্ড আপডেট ও শো করা
        document.getElementById('res-name').innerText = document.getElementById('student-name-input').value;
        document.getElementById('score').innerText = totalScore;
        document.getElementById('result-box').style.display = 'block';

        // স্ক্রিনটি স্ক্রোল করে টপে নিয়ে যাওয়া যাতে রেজাল্ট ও ব্যাখ্যা একবারে দেখা যায়
        window.scrollTo({top: 0, behavior: 'smooth'});
    }
</script>

</body>
</html>

        <h3>পরীক্ষার্থীর নাম লিখুন:</h3>
        <input type="text" id="student-name-input" class="input-field" placeholder="আপনার সম্পূর্ণ নাম..." autocomplete="off">
        <br>
        <button class="btn" onclick="startExam()">পরীক্ষা শুরু করো</button>
    </div>

    <div id="exam-screen" style="display: none;">
        <div class="exam-header">
            <div>পরীক্ষার্থী: <span id="display-student-name" style="color: #1a73e8;"></span></div>
            <div class="timer-box">সময় বাকি: <span id="timer">10:00</span></div>
        </div>

        <div id="result-box" class="result-box">
            <h2>🎉 পরীক্ষার ফলাফল 🎉</h2>
            <p style="font-size: 18px;">পরীক্ষার্থী: <span id="res-name" style="font-weight: bold;"></span></p>
            <p style="font-size: 24px; font-weight: bold;">মোট স্কোর: <span id="score">0</span> / ১০</p>
            <p style="font-size: 16px; color: #5f6368;">নিচে আপনার উত্তরপত্র পর্যালোচনা করুন।</p>
        </div>

        <form id="quiz-form">
            <div class="question-card" data-qnum="1">
                <p class="question-text">১. পাখির पैरों মতো বদ্বীপ দেখা যায় যে নদীর মোহանায়-</p>
                <div class="options-container">
                    <label class="option-label"><input type="radio" name="q1" value="correct">(ক) মিসিসিপি-মিসৌরি</label>
                    <label class="option-label"><input type="radio" name="q1" value="wrong">(খ) হোয়াংহো</label>
                    <label class="option-label"><input type="radio" name="q1" value="wrong">(গ) ইরাবতী</label>
                    <label class="option-label"><input type="radio" name="q1" value="wrong">(ঘ) তাইবার</label>
                </div>
                <div class="explanation-box" id="exp-1">
                    <strong>সঠিক উত্তর: (ক) মিসিসিপি-মিসৌরি</strong><br>
                    ব্যাখ্যা: মিসিসিপি-মিসৌরি নদীর মোহানায় নদীস্রোত ও সমুদ্রস্রোতের পারস্পরিক প্রভাবে পলি সঞ্চিত হয়ে ঠিক পাখির পায়ের মতো দেখতে একটি বদ্বীপ গঠিত হয়েছে।
                </div>
            </div>

            <div class="question-card" data-qnum="2">
                <p class="question-text">২. বায়ুমণ্ডলের যে স্তরে আবহাওয়ার গোলযোগ দেখা যায় সেই স্তরটি হলো-</p>
                <div class="options-container">
                    <label class="option-label"><input type="radio" name="q2" value="wrong">(ক) স্ট্র্যাটোস্ফিয়ার</label>
                    <label class="option-label"><input type="radio" name="q2" value="wrong">(খ) মেসোস্ফিয়ার</label>
                    <label class="option-label"><input type="radio" name="q2" value="correct">(গ) トロポস্ফিয়ার</label>
                    <label class="option-label"><input type="radio" name="q2" value="wrong">(ঘ) আয়নোস্ফিয়ার</label>
                </div>
                <div class="explanation-box" id="exp-2">
                    <strong>সঠিক উত্তর: (গ) ট্রপোস্ফিয়ার</strong><br>
                    ব্যাখ্যা: ট্রপোস্ফিয়ার হলো বায়ুমণ্ডলের সবচেয়ে নীচের স্তর। ধূলিকণা ও জলীয় বাষ্পের প্রায় পুরোটাই এই স্তরে থাকায় মেঘ, ঝড়, বৃষ্টি, বজ্রপাত ইত্যাদি যাবতীয় আবহাওয়াগত গোলযোগ বা অশান্ত অবস্থা এই স্তরেই ঘটে। এই কারণে একে 'ক্ষুব্ধমণ্ডল' বলা হয়।
                </div>
            </div>

            <div class="question-card" data-qnum="3">
                <p class="question-text">৩. সমুদ্রের যে স্থানে উষ্ণ ও শীতল স্রোত উভয়ে মিলিত হয় তাকে বলে-</p>
                <div class="options-container">
                    <label class="option-label"><input type="radio" name="q3" value="wrong">(ক) হিমানী সম্প্রপাত</label>
                    <label class="option-label"><input type="radio" name="q3" value="wrong">(খ) হিমশৈল</label>
                    <label class="option-label"><input type="radio" name="q3" value="correct">(গ) হিমপ্রাচীর</label>
                    <label class="option-label"><input type="radio" name="q3" value="wrong">(ঘ) হিমগুল্ম</label>
                </div>
                <div class="explanation-box" id="exp-3">
                    <strong>সঠিক উত্তর: (গ) হিমপ্রাচীর</strong><br>
                    ব্যাখ্যা: সমুদ্রের যেখানে উষ্ণ ও শীতল স্রোত মিলিত হয়, সেখানে দুই স্রোতের জলের রং ও ঘনত্বের পার্থক্যের জন্য একটি স্পষ্ট সীমারেখা বা প্রাচীরের মতো অংশ দেখা যায়। একেই হিমপ্রাচীর বলে।
                </div>
            </div>

            <div class="question-card" data-qnum="4">
                <p class="question-text">৪. ল্যান্ডফিল বা ভরাটকরণ থেকে উৎপন্ন গ্যাসটি হল-</p>
                <div class="options-container">
                    <label class="option-label"><input type="radio" name="q4" value="wrong">(ক) অক্সিজেন</label>
                    <label class="option-label"><input type="radio" name="q4" value="wrong">(খ) কার্বন মনোঅক্সাইড</label>
                    <label class="option-label"><input type="radio" name="q4" value="wrong">(গ) অ্যামোনিয়া</label>
                    <label class="option-label"><input type="radio" name="q4" value="correct">(ঘ) মিথেন</label>
                </div>
                <div class="explanation-box" id="exp-4">
                    <strong>সঠিক উত্তর: (ঘ) মিথেন</strong><br>
                    ব্যাখ্যা: বর্জ্য ভরাটকরণ বা ল্যান্ডফিল পদ্ধতিতে নিচু জমিতে জমা করা জৈব বর্জ্যগুলি মাটির নীচে অবায়বীয় ব্যাকটেরিয়া দ্বারা পচে গিয়ে প্রধানত মিথেন গ্যাস উৎপন্ন করে।
                </div>
            </div>

            <div class="question-card" data-qnum="5">
                <p class="question-text">৫. ভারতের 'সিলিকন ভ্যালি' বলা হয়-</p>
                <div class="options-container">
                    <label class="option-label"><input type="radio" name="q5" value="wrong">(ক) কলকাতা</label>
                    <label class="option-label"><input type="radio" name="q5" value="wrong">(খ) মুম্বাই</label>
                    <label class="option-label"><input type="radio" name="q5" value="correct">(গ) বেঙ্গালুরু</label>
                    <label class="option-label"><input type="radio" name="q5" value="wrong">(ঘ) দিল্লি</label>
                </div>
                <div class="explanation-box" id="exp-5">
                    <strong>সঠিক উত্তর: (গ) বেঙ্গালুরু</strong><br>
                    ব্যাখ্যা: মার্কিন যুক্তরাষ্ট্রের ক্যালিফোর্নিয়ার সিলিকন ভ্যালির মতো ভারতের কর্ণাটক রাজ্যের বেঙ্গালুরু শহরে সিলিকন ভিত্তিক তথ্যপ্রযুক্তি শিল্পের সর্বাধিক বিকাশ ঘটেছে।
                </div>
            </div>

            <div class="question-card" data-qnum="6">
                <p class="question-text">৬. ভারতের দীর্ঘতম সেচখাল কোনটি?</p>
                <div class="options-container">
                    <label class="option-label"><input type="radio" name="q6" value="wrong">(ক) উচ্চ গঙ্গা খাল</label>
                    <label class="option-label"><input type="radio" name="q6" value="wrong">(খ) সিরহিন্দ খাল</label>
                    <label class="option-label"><input type="radio" name="q6" value="correct">(গ) ইন্দিরা গান্ধী খাল</label>
                    <label class="option-label"><input type="radio" name="q6" value="wrong">(ঘ) দামোদর খাল</label>
                </div>
                <div class="explanation-box" id="exp-6">
                    <strong>সঠিক উত্তর: (গ) ইন্দিরা গান্ধী খাল</strong><br>
                    ব্যাখ্যা: রাজস্থানের ইন্দিরা গান্ধী খাল (যার দৈর্ঘ্য প্রায় ৫৮২ কিমি) হলো ভারতের দীর্ঘতম সেচখাল।
                </div>
            </div>

            <div class="question-card" data-qnum="7">
                <p class="question-text">৭. দক্ষিণ ভারতের সর্বোচ্চ পর্বতশৃঙ্গ হলো-</p>
                <div class="options-container">
                    <label class="option-label"><input type="radio" name="q7" value="wrong">(ক) দোদাবেতা</label>
                    <label class="option-label"><input type="radio" name="q7" value="wrong">(খ) অমরকণ্টক</label>
                    <label class="option-label"><input type="radio" name="q7" value="correct">(গ) আনাইমুদি</label>
                    <label class="option-label"><input type="radio" name="q7" value="wrong">(ঘ) মহেন্দ্রগিরি</label>
                </div>
                <div class="explanation-box" id="exp-7">
                    <strong>সঠিক উত্তর: (গ) আনাইমুদি</strong><br>
                    ব্যাখ্যা: আনাইমুদি (২৬৯০ মিটার) আন্নামালাই পর্বতে অবস্থিত, যা সমগ্র দক্ষিণ ভারতের সর্বোচ্চ শৃঙ্গ।
                </div>
            </div>

            <div class="question-card" data-qnum="8">
                <p class="question-text">৮. উপগ্রহ চিত্রে গভীর বনভূমি বা উদ্ভিদ বোঝাতে কোন ছদ্ম রং (False Colour) ব্যবহার করা হয়?</p>
                <div class="options-container">
                    <label class="option-label"><input type="radio" name="q8" value="wrong">(ক) সবুজ</label>
                    <label class="option-label"><input type="radio" name="q8" value="correct">(খ) লাল বা গাঢ় লাল</label>
                    <label class="option-label"><input type="radio" name="q8" value="wrong">(গ) গাঢ় নীল</label>
                    <label class="option-label"><input type="radio" name="q8" value="wrong">(ঘ) হলুদ</label>
                </div>
                <div class="explanation-box" id="exp-8">
                    <strong>সঠিক উত্তর: (খ) লাল বা গাঢ় লাল</strong><br>
                    ব্যাখ্যা: উপগ্রহ চিত্রে সেন্সরে ইনফ্রারেড রশ্মির প্রতিফলনের কারণে সবুজ উদ্ভিদ বা গভীর অরণ্যকে লাল বা গাঢ় লাল রঙে দেখানো হয়।
                </div>
            </div>

            <div class="question-card" data-qnum="9">
                <p class="question-text">৯. মরা কোটাল বা মরা জোয়ার কোন তিথিতে সৃষ্টি হয়?</p>
                <div class="options-container">
                    <label class="option-label"><input type="radio" name="q9" value="wrong">(ক) পূর্ণিমা</label>
                    <label class="option-label"><input type="radio" name="q9" value="wrong">(খ) অমাবস্যা</label>
                    <label class="option-label"><input type="radio" name="q9" value="correct">(গ) শুক্ল ও কৃষ্ণপক্ষের অষ্টমী</label>
                    <label class="option-label"><input type="radio" name="q9" value="wrong">(ঘ) একাদশী</label>
                </div>
                <div class="explanation-box" id="exp-9">
                    <strong>সঠিক উত্তর: (গ) শুক্ল ও কৃষ্ণপক্ষের অষ্টমী</strong><br>
                    ব্যাখ্যা: শুক্ল ও কৃষ্ণপক্ষের অষ্টমী তিথিতে চাঁদ ও সূর্য পৃথিবীর সাপেক্ষে সমকোণে অবস্থান করে। এর ফলে সমুদ্রের জলস্ফীতি অনেক কম হয়, যাকে মরা কোটাল বলে।
                </div>
            </div>

            <div class="question-card" data-qnum="10">
                <p class="question-text">১০. ভারতের মহাকাশ গবেষণা সংস্থা (ISRO)-এর সদর দপ্তর কোথায় অবস্থিত?</p>
                <div class="options-container">
                    <label class="option-label"><input type="radio" name="q10" value="wrong">(ক) দিল্লি</label>
                    <label class="option-label"><input type="radio" name="q10" value="wrong">(খ) চেন্নাই</label>
                    <label class="option-label"><input type="radio" name="q10" value="correct">(গ) বেঙ্গালুরু</label>
                    <label class="option-label"><input type="radio" name="q10" value="wrong">(ঘ) কলকাতা</label>
                </div>
                <div class="explanation-box" id="exp-10">
                    <strong>সঠিক উত্তর: (গ) বেঙ্গালুরু</strong><br>
                    ব্যাখ্যা: ভারতের মহাকাশ গবেষণা সংস্থা ISRO-এর প্রধান কার্যালয় বা সদর দপ্তর কর্ণাটকের বেঙ্গালুরু শহরে অবস্থিত।
                </div>
            </div>

            <div style="text-align: center; margin-top: 30px; margin-bottom: 5px;">
                <button type="button" id="submit-btn" class="btn" style="background-color: #34a853;" onclick="submitExam()">খাতা জমা দিন (Submit)</button>
            </div>
        </form>
    </div>
</div>

<script>
    let totalTime = 600; // ১০ মিনিট সেকেন্ডে (10 * 60)
    let timerInterval;

    // পরীক্ষা শুরু করার ফাংশন
    function startExam() {
        const nameInput = document.getElementById('student-name-input').value.trim();
        if (nameInput === "") {
            alert("দয়া করে পরীক্ষা শুরু করার আগে আপনার নাম লিখুন!");
            return;
        }

        // স্ক্রিন অদলবদল
        document.getElementById('start-screen').style.display = 'none';
        document.getElementById('exam-screen').style.display = 'block';
        document.getElementById('display-student-name').innerText = nameInput;

        // টাইমার চালু করা
        timerInterval = setInterval(updateTimer, 1000);
    }

    // টাইমার কাউন্টডাউন ফাংশন
    function updateTimer() {
        let minutes = Math.floor(totalTime / 60);
        let seconds = totalTime % 60;

        seconds = seconds < 10 ? '0' + seconds : seconds;
        minutes = minutes < 10 ? '0' + minutes : minutes;

        document.getElementById('timer').innerText = minutes + ":" + seconds;

        if (totalTime <= 0) {
            clearInterval(timerInterval);
            alert("সময় শেষ! আপনার উত্তরপত্রটি স্বয়ংক্রিয়ভাবে জমা নেওয়া হলো।");
            submitExam(); // টাইম শেষ হলে অটোমেটিক সাবমিট
        }
        totalTime--;
    }

    // পরীক্ষা জমা দেওয়ার মেইন ফাংশন
    function submitExam() {
        clearInterval(timerInterval); // টাইমার স্টপ
        document.getElementById('submit-btn').style.display = 'none'; // সাবমিট বাটন হাইড
        document.getElementById('timer').innerText = "00:00 (জমা দেওয়া হয়েছে)";

        const form = document.getElementById('quiz-form');
        let totalScore = 0;

        // ১ থেকে ১০ পর্যন্ত প্রতিটি কার্ড লুপ করা
        const cards = document.getElementsByClassName('question-card');
        
        for (let card of cards) {
            const qNum = card.getAttribute('data-qnum');
            const radioButtons = form.elements['q' + qNum];
            const labels = card.getElementsByClassName('option-label');
            
            let selectedValue = "";

            // ছাত্র কোন অপশন সিলেক্ট করেছে এবং সঠিক বাটন লক করা
            for (let i = 0; i < radioButtons.length; i++) {
                radioButtons[i].disabled = true; // লক করা হচ্ছে
                
                if (radioButtons[i].checked) {
                    selectedValue = radioButtons[i].value;
                }

                // সঠিক উত্তরের ব্যাকগ্রাউন্ড সবুজ করা
                if (radioButtons[i].value === "correct") {
                    labels[i].classList.add('correct');
                }
                
                // ছাত্র যদি ভুল উত্তর সিলেক্ট করে থাকে তবে লাল করা
                if (radioButtons[i].checked && radioButtons[i].value === "wrong") {
                    labels[i].classList.add('wrong');
                }
            }

            // স্কোর হিসেব করা
            if (selectedValue === "correct") {
                totalScore++;
            }

            // এই প্রশ্নের ব্যাখ্যা বক্সটি ওপেন করা
            document.getElementById('exp-' + qNum).style.display = 'block';
        }

        // রেজাল্ট ড্যাশবোর্ড আপডেট ও শো করা
        document.getElementById('res-name').innerText = document.getElementById('student-name-input').value;
        document.getElementById('score').innerText = totalScore;
        document.getElementById('result-box').style.display = 'block';

        // স্ক্রিনটি স্ক্রোল করে টপে নিয়ে যাওয়া যাতে রেজাল্ট ও ব্যাখ্যা একবারে দেখা যায়
        window.scrollTo({top: 0, behavior: 'smooth'});
    }
</script>

</body>
</html>

            <button class="option-btn" onclick="checkAns(this, false, 3)">(ঘ) হিমগুল্ম</button>
        </div>
        <div class="explanation-box" id="exp-3">
            <strong>সঠিক উত্তর: (গ) হিমপ্রাচীর</strong><br>
            ব্যাখ্যা: সমুদ্রের যেখানে উষ্ণ ও শীতল স্রোত মিলিত হয়, সেখানে দুই স্রোতের জলের রং ও ঘনত্বের পার্থক্যের জন্য একটি স্পষ্ট সীমারেখা বা প্রাচীরের মতো অংশ দেখা যায়। একেই হিমপ্রাচীর বলে। যেমন, আটলান্টিক মহাসাগরে উষ্ণ উপসাগরীয় স্রোত (গাঢ় নীল) ও শীতল ল্যাব্রাডর স্রোতের (সবুজ) মাঝে এটি দেখা যায়।
        </div>
    </div>

    <div class="question-card">
        <p class="question-text">৪. ল্যান্ডফিল বা ভরাটকরণ থেকে উৎপন্ন গ্যাসটি হল-</p>
        <div class="options-container">
            <button class="option-btn" onclick="checkAns(this, false, 4)">(ক) অক্সিজেন</button>
            <button class="option-btn" onclick="checkAns(this, false, 4)">(খ) কার্বন মনোঅক্সাইড</button>
            <button class="option-btn" onclick="checkAns(this, false, 4)">(গ) অ্যামোনিয়া</button>
            <button class="option-btn" onclick="checkAns(this, true, 4)">(ঘ) মিথেন</button>
        </div>
        <div class="explanation-box" id="exp-4">
            <strong>সঠিক উত্তর: (ঘ) মিথেন</strong><br>
            ব্যাখ্যা: বর্জ্য ভরাটকরণ বা ল্যান্ডফিল পদ্ধতিতে নিচু জমিতে জমা করা জৈব বর্জ্যগুলি মাটির নীচে অবায়বীয় ব্যাকটেরিয়া দ্বারা পচে গিয়ে প্রধানত মিথেন গ্যাস উৎপন্ন করে, যা অত্যন্ত দাহ্য এবং গ্রিনহাউস গ্যাস হিসেবে পরিচিত।
        </div>
    </div>

    <div class="question-card">
        <p class="question-text">৫. ভারতের 'সিলিকন ভ্যালি' বলা হয়-</p>
        <div class="options-container">
            <button class="option-btn" onclick="checkAns(this, false, 5)">(ক) কলকাতা</button>
            <button class="option-btn" onclick="checkAns(this, false, 5)">(খ) মুম্বাই</button>
            <button class="option-btn" onclick="checkAns(this, true, 5)">(গ) বেঙ্গালুরু</button>
            <button class="option-btn" onclick="checkAns(this, false, 5)">(ঘ) দিল্লি</button>
        </div>
        <div class="explanation-box" id="exp-5">
            <strong>সঠিক উত্তর: (গ) বেঙ্গালুরু</strong><br>
            ব্যাখ্যা: মার্কিন যুক্তরাষ্ট্রের ক্যালিফোর্নিয়ার সিলিকন ভ্যালির মতো ভারতের কর্ণাটক রাজ্যের বেঙ্গালুরু শহরে সিলিকন ভিত্তিক তথ্যপ্রযুক্তি ও ইলেকট্রনিকস শিল্পের সর্বাধিক বিকাশ ঘটেছে। তাই একে ভারতের সিলিকন ভ্যালি বলা হয়।
        </div>
    </div>

    <div class="question-card">
        <p class="question-text">৬. ভারতের দীর্ঘতম সেচখাল কোনটি?</p>
        <div class="options-container">
            <button class="option-btn" onclick="checkAns(this, false, 6)">(ক) উচ্চ গঙ্গা খাল</button>
            <button class="option-btn" onclick="checkAns(this, false, 6)">(খ) সিরহিন্দ খাল</button>
            <button class="option-btn" onclick="checkAns(this, true, 6)">(গ) ইন্দিরা গান্ধী খাল</button>
            <button class="option-btn" onclick="checkAns(this, false, 6)">(ঘ) দামোদর খাল</button>
        </div>
        <div class="explanation-box" id="exp-6">
            <strong>সঠিক উত্তর: (গ) ইন্দিরা গান্ধী খাল</strong><br>
            ব্যাখ্যা: রাজস্থানের ইন্দিরা গান্ধী খাল (যার দৈর্ঘ্য প্রায় ৫৮২ কিমি) হলো ভারতের দীর্ঘতম সেচখাল। এর সাহায্যে রাজস্থানের শুষ্ক ও মরু অঞ্চলে কৃষিকাজে জলসেচ করা সম্ভব হয়েছে।
        </div>
    </div>

    <div class="question-card">
        <p class="question-text">৭. দক্ষিণ ভারতের সর্বোচ্চ পর্বতশৃঙ্গ হলো-</p>
        <div class="options-container">
            <button class="option-btn" onclick="checkAns(this, false, 7)">(ক) দোদাবেতা</button>
            <button class="option-btn" onclick="checkAns(this, false, 7)">(খ) অমরকণ্টক</button>
            <button class="option-btn" onclick="checkAns(this, true, 7)">(গ) আনাইমুদি</button>
            <button class="option-btn" onclick="checkAns(this, false, 7)">(ঘ) মহেন্দ্রগিরি</button>
        </div>
        <div class="explanation-box" id="exp-7">
            <strong>সঠিক উত্তর: (গ) আনাইমুদি</strong><br>
            ব্যাখ্যা: আনাইমুদি (২৬৯০ মিটার) আন্নামালাই পর্বতে অবস্থিত, যা সমগ্র দক্ষিণ ভারতের সর্বোচ্চ শৃঙ্গ। অন্যদিকে দোদাবেতা হলো নীলগিরি পর্বতের সর্বোচ্চ শৃঙ্গ।
        </div>
    </div>

    <div class="question-card">
        <p class="question-text">৮. উপগ্রহ চিত্রে গভীর বনভূমি বা উদ্ভিদ বোঝাতে কোন ছদ্ম রং (False Colour) ব্যবহার করা হয়?</p>
        <div class="options-container">
            <button class="option-btn" onclick="checkAns(this, false, 8)">(ক) সবুজ</button>
            <button class="option-btn" onclick="checkAns(this, true, 8)">(খ) লাল বা গাঢ় লাল</button>
            <button class="option-btn" onclick="checkAns(this, false, 8)">(গ) গাঢ় নীল</button>
            <button class="option-btn" onclick="checkAns(this, false, 8)">(ঘ) হলুদ</button>
        </div>
        <div class="explanation-box" id="exp-8">
            <strong>সঠিক উত্তর: (খ) লাল বা গাঢ় লাল</strong><br>
            ব্যাখ্যা: উপগ্রহ চিত্রে (FCC) বস্তুর প্রকৃত রঙের পরিবর্তে ছদ্ম রং ব্যবহার করা হয়। এখানে সেন্সরে ইনফ্রারেড বা অবলোহিত রশ্মির প্রতিফলনের কারণে সবুজ উদ্ভিদ বা গভীর অরণ্যকে লাল বা গাঢ় লাল রঙে দেখানো হয়।
        </div>
    </div>

    <div class="question-card">
        <p class="question-text">৯. মরা কোটাল বা মরা জোয়ার কোন তিথিতে সৃষ্টি হয়?</p>
        <div class="options-container">
            <button class="option-btn" onclick="checkAns(this, false, 9)">(ক) পূর্ণিমা</button>
            <button class="option-btn" onclick="checkAns(this, false, 9)">(খ) অমাবস্যা</button>
            <button class="option-btn" onclick="checkAns(this, true, 9)">(গ) শুক্ল ও কৃষ্ণপক্ষের অষ্টমী</button>
            <button class="option-btn" onclick="checkAns(this, false, 9)">(ঘ) একাদশী</button>
        </div>
        <div class="explanation-box" id="exp-9">
            <strong>সঠিক উত্তর: (গ) শুক্ল ও কৃষ্ণপক্ষের অষ্টমী</strong><br>
            ব্যাখ্যা: শুক্ল ও কৃষ্ণপক্ষের অষ্টমী তিথিতে চাঁদ ও সূর্য পৃথিবীর সাপেক্ষে সমকোণে (৯০° কোণে) অবস্থান করে। এর ফলে চাঁদ ও সূর্যের আকর্ষণ বল পরস্পর বিরোধী হয় এবং সমুদ্রের জলস্ফীতি অনেক কম হয়, যাকে মরা কোটাল বলে।
        </div>
    </div>

    <div class="question-card">
        <p class="question-text">১০. ভারতের মহাকাশ গবেষণা সংস্থা (ISRO)-এর সদর দপ্তর কোথায় অবস্থিত?</p>
        <div class="options-container">
            <button class="option-btn" onclick="checkAns(this, false, 10)">(ক) দিল্লি</button>
            <button class="option-btn" onclick="checkAns(this, false, 10)">(খ) চেন্নাই</button>
            <button class="option-btn" onclick="checkAns(this, true, 10)">(গ) বেঙ্গালুরু</button>
            <button class="option-btn" onclick="checkAns(this, false, 10)">(ঘ) কলকাতা</button>
        </div>
        <div class="explanation-box" id="exp-10">
            <strong>সঠিক উত্তর: (গ) বেঙ্গালুরু</strong><br>
            ব্যাখ্যা: ভারতের মহাকাশ গবেষণা সংস্থা ISRO (Indian Space Research Organisation)-এর প্রধান কার্যালয় বা সদর দপ্তর কর্ণাটকের বেঙ্গালুরু শহরে অবস্থিত। এখান থেকেই ভারতের উপগ্রহ চিত্র এবং মহাকাশ সংক্রান্ত গবেষণা পরিচালিত হয়।
        </div>
    </div>

</div>

<script>
    function checkAns(button, isCorrect, qNum) {
        // প্রশ্নকার্ডের ভেতরের সব বাটন সিলেক্ট করা
        const container = button.parentElement;
        const buttons = container.getElementsByClassName('option-btn');
        
        // একবার ক্লিক করার পর ওই প্রশ্নের বাকি বাটন লক করে দেওয়া
        for (let btn of buttons) {
            btn.disabled = true;
            // ব্যবহারকারী ক্লিক না করলেও যদি ওটা সঠিক উত্তর হয়, তবে চিহ্নিত করার জন্য
            if (btn.getAttribute('onclick').includes('true')) {
                btn.classList.add('correct');
            }
        }
        
        // ব্যবহারকারী ভুল ক্লিক করলে লাল রঙ দেখানো
        if (!isCorrect) {
            button.classList.add('wrong');
        }
        
        // ব্যাখ্যা (Explanation) বক্সটি ওপেন করা
        const expBox = document.getElementById('exp-' + qNum);
        expBox.style.display = 'block';
    }
</script>

</body>
</html>
