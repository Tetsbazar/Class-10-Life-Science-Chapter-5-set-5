<!DOCTYPE html>
<html lang="bn">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>জীবন বিজ্ঞান কুইজ - অধ্যায় ৫ (সেট ৫ - ১০ মিনিট)</title>
    <style>
        :root {
            --primary-color: #27ae60;
            --primary-hover: #1e8449;
            --bg-color: #f4f9f4;
            --text-color: #2c3e50;
            --card-bg: #ffffff;
            --correct-color: #2ecc71;
            --wrong-color: #e74c3c;
            --timer-color: #d35400;
            --admin-color: #8e44ad;
            --next-set-color: #2980b9;
            --next-set-hover: #3498db;
        }

        body {
            font-family: 'Segoe UI', Arial, sans-serif;
            background-color: var(--bg-color);
            color: var(--text-color);
            margin: 0;
            padding: 20px;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
        }

        .container {
            background-color: var(--card-bg);
            width: 100%;
            max-width: 800px;
            padding: 40px 30px;
            border-radius: 12px;
            box-shadow: 0 10px 30px rgba(39, 174, 96, 0.08);
            position: relative;
            height: fit-content;
        }

        h1 {
            text-align: center;
            color: var(--primary-hover);
            margin-bottom: 5px;
            font-size: 1.8em;
        }

        .subtitle {
            text-align: center;
            color: #7f8c8d;
            margin-bottom: 25px;
            font-size: 1em;
        }

        /* Login Section Styles */
        #login-section {
            display: block;
            max-width: 400px;
            margin: 0 auto;
        }

        .form-group {
            margin-bottom: 20px;
        }

        .form-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: bold;
            color: #555;
        }

        .form-group input {
            width: 100%;
            padding: 12px 15px;
            border: 2px solid #e9ecef;
            border-radius: 8px;
            font-size: 1.1em;
            box-sizing: border-box;
            transition: border-color 0.3s ease;
        }

        .form-group input:focus {
            border-color: var(--primary-color);
            outline: none;
        }

        .error-message {
            color: var(--wrong-color);
            text-align: center;
            font-weight: bold;
            margin-bottom: 15px;
            display: none;
        }

        /* Quiz, Admin & Limit Block Sections */
        #quiz-section, #admin-section, #limit-section {
            display: none;
        }

        .limit-box {
            text-align: center;
            padding: 30px;
            background-color: #fce4d6;
            border: 2px solid #f1948a;
            border-radius: 8px;
            color: #c0392b;
            font-size: 1.2em;
            font-weight: bold;
            margin-bottom: 20px;
        }

        .question-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
            font-weight: bold;
            color: #7f8c8d;
        }

        .timer-box {
            background-color: #fdf2e9;
            color: var(--timer-color);
            padding: 6px 15px;
            border-radius: 20px;
            border: 1px solid #fadbd8;
            font-size: 1.1em;
            display: flex;
            align-items: center;
            gap: 5px;
        }

        .question-text {
            font-size: 1.25em;
            font-weight: 600;
            margin-bottom: 20px;
            line-height: 1.5;
        }

        .options-list {
            list-style: none;
            padding: 0;
            margin: 0;
        }

        .option-item {
            background-color: #f8f9fa;
            border: 2px solid #e9ecef;
            border-radius: 8px;
            padding: 15px 20px;
            margin-bottom: 12px;
            font-size: 1.1em;
            cursor: pointer;
            transition: all 0.2s ease;
        }

        .option-item:hover {
            border-color: var(--primary-color);
            background-color: #f4fbf6;
        }

        .option-item.selected {
            background-color: var(--primary-color);
            color: white;
            border-color: var(--primary-color);
        }

        .btn {
            background-color: var(--primary-color);
            color: white;
            border: none;
            padding: 15px 30px;
            font-size: 1.1em;
            font-weight: bold;
            border-radius: 8px;
            cursor: pointer;
            width: 100%;
            margin-top: 10px;
            transition: background-color 0.3s ease;
        }

        .btn:hover {
            background-color: var(--primary-hover);
        }

        /* Next Set Link Button */
        .btn-next-set {
            background-color: var(--next-set-color);
            text-align: center;
            text-decoration: none;
            display: block;
            box-sizing: border-box;
            font-size: 1.1em;
            font-weight: bold;
            color: white;
            padding: 15px 30px;
            border-radius: 8px;
            margin-top: 10px;
            transition: background-color 0.3s ease;
        }

        .btn-next-set:hover {
            background-color: var(--next-set-hover);
        }

        /* Admin Dashboard Table */
        .admin-title {
            color: var(--admin-color) !important;
        }
        
        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 20px;
            font-size: 1.05em;
        }

        th, td {
            border: 1px solid #e2e8f0;
            padding: 12px 15px;
            text-align: left;
        }

        th {
            background-color: #f1f5f9;
            color: #334155;
            font-weight: bold;
        }

        tr:nth-child(even) {
            background-color: #f8fafc;
        }

        /* Results Display */
        #result-section {
            display: none;
        }

        .score-board {
            text-align: center;
            padding: 20px;
            background: linear-gradient(135deg, #eaf2e8, #d5ebd5);
            border-radius: 10px;
            margin-bottom: 20px;
        }

        .score-board h2 {
            margin: 0;
            color: #2c3e50;
            font-size: 1.8em;
        }

        .review-item {
            background-color: #fdfdfd;
            border: 1px solid #e0e0e0;
            border-radius: 8px;
            padding: 20px;
            margin-bottom: 20px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.02);
        }

        .review-q {
            font-size: 1.1em;
            font-weight: bold;
            margin-bottom: 15px;
        }

        .review-ans {
            margin-bottom: 8px;
            font-size: 1em;
        }

        .ans-correct { color: var(--correct-color); font-weight: bold; }
        .ans-wrong { color: var(--wrong-color); font-weight: bold; }

        .explanation {
            background-color: #fff9e6;
            border-left: 4px solid #f1c40f;
            padding: 12px 15px;
            margin-top: 15px;
            font-size: 0.95em;
            color: #555;
            border-radius: 0 4px 4px 0;
        }

        .welcome-text {
            color: var(--primary-hover);
            font-weight: bold;
        }
    </style>
</head>
<body>

<div class="container">

    <!-- Login Section -->
    <div id="login-section">
        <h1>স্টুডেন্ট ও অ্যাডমিন লগইন</h1>
        <p class="subtitle">জীবন বিজ্ঞান প্র্যাকটিস সেট শুরু করতে নিচে লগইন করুন</p>

        <div class="form-group">
            <label for="username">ইউজারনেম (Username)</label>
            <input type="text" id="username" placeholder="আপনার ইউজারনেম দিন" autocomplete="off">
        </div>

        <div class="form-group">
            <label for="password">পাসওয়ার্ড (Password)</label>
            <input type="password" id="password" placeholder="আপনার গোপন পাসওয়ার্ড দিন">
        </div>

        <div class="error-message" id="error-message">ইউজারনেম অথবা পাসওয়ার্ড ভুল হয়েছে!</div>

        <button class="btn" id="login-btn">লগইন করুন</button>
    </div>

    <!-- Attempt Limit Exceeded Section -->
    <div id="limit-section">
        <div class="limit-box">
            ⚠️ দুঃখিত, আপনার এই সেটের জন্য নির্ধারিত ১০ বার পরীক্ষার লিমিট শেষ হয়ে গেছে!
        </div>
        <p style="text-align: center; color: #555;">আপনি আর নতুন করে এই কুইজটিতে অংশগ্রহণ করতে পারবেন না। পরবর্তী সুযোগের জন্য আপনার শিক্ষকের সাথে যোগাযোগ করুন।</p>
        <button class="btn" onclick="location.reload()">লগ আউট ও ফিরে যান</button>
    </div>

    <!-- Admin Panel Section -->
    <div id="admin-section">
        <h1 class="admin-title">📊 শিক্ষক ড্যাশবোর্ড (Admin Panel)</h1>
        <p class="subtitle">পরীক্ষার্থীদের লাইভ পারফরম্যান্স ও মক টেস্টের ফুল রিপোর্ট (সর্বোচ্চ ১০ বার লিমিট)</p>
        
        <table>
            <thead>
                <tr>
                    <th>ছাত্রের নাম (Username)</th>
                    <th>সর্বোচ্চ স্কোর (Best Score)</th>
                    <th>মোট কতবার দিয়েছে (Total Attempts)</th>
                    <th>স্ট্যাটাস (Status)</th>
                </tr>
            </thead>
            <tbody id="admin-table-body">
                <!-- Data injected via JS -->
            </tbody>
        </table>
        
        <button class="btn" style="background-color: var(--admin-color); margin-top: 30px;" onclick="clearReports()">সমস্ত রেকর্ড ও লিমিট রিসেট করুন</button>
        <button class="btn" onclick="location.reload()">লগ আউট করুন</button>
    </div>

    <!-- Quiz Section -->
    <div id="quiz-section">
        <h1>জীবন বিজ্ঞান কুইজ: অধ্যায় ৫</h1>
        <div class="subtitle">
            <span class="welcome-text">পরীক্ষার্থী: <span id="student-name"></span></span> | সেট ৫: পরিবেশ এবং মানব জনসমষ্টি
        </div>

        <div class="question-header">
            <span id="q-counter">প্রশ্ন: ১ / ১৫</span>
            <div class="timer-box">
                ⏱️ সময় বাকি: <span id="timer-display">10:00</span>
            </div>
        </div>

        <div class="question-text" id="question-text">এখানে প্রশ্ন আসবে</div>
        <ul class="options-list" id="options-list">
            <!-- Options via JS -->
        </ul>

        <button class="btn" id="next-btn">পরবর্তী প্রশ্ন</button>
    </div>

    <!-- Result Section -->
    <div id="result-section">
        <div class="score-board">
            <h2>পরীক্ষা সম্পন্ন হয়েছে, <span id="result-student-name"></span>!</h2>
            <h1 style="margin-top: 10px;" id="final-score">স্কোর: 0 / 15</h1>
        </div>

        <!-- Set 6 Real Link Added Here -->
        <a href="https://tetsbazar.github.io/Class-10-Life-Science-Chapter-5-Set-6" target="_blank" class="btn-next-set">
            👉 পরবর্তী মক টেস্ট (সেট - ৬) দেওয়ার জন্য এখানে ক্লিক করুন
        </a>

        <h3 style="margin-top: 30px;">প্রশ্নের বিস্তারিত পর্যালোচনা:</h3>
        <div id="review-container">
            <!-- Review items via JS -->
        </div>
        <button class="btn" onclick="location.reload()">লগ আউট করুন</button>
    </div>

</div>

<script>
    // --- Login System Database ---
    const approvedStudents = {
        "anil7890": "12345677",
        "samir7890": "12345666",
        "rahul2024": "pass1234",
        "rohit999": "88889999",
        "suman007": "abcdef12",
        "Dhiren": "Dhiren1234",
        "Pradip": "Pradip1234",
        "Bijay": "Bijay1234",
        "admin": "admin1234" 
    };

    const attemptLimit = 10; // Maximum allowed exam attempts per student

    const loginSection = document.getElementById("login-section");
    const quizSection = document.getElementById("quiz-section");
    const adminSection = document.getElementById("admin-section");
    const limitSection = document.getElementById("limit-section");
    const adminTableBody = document.getElementById("admin-table-body");
    const usernameInput = document.getElementById("username");
    const passwordInput = document.getElementById("password");
    const loginBtn = document.getElementById("login-btn");
    const errorMessage = document.getElementById("error-message");
    const studentNameDisplay = document.getElementById("student-name");
    const resultStudentName = document.getElementById("result-student-name");

    let currentUsername = "";

    loginBtn.addEventListener("click", () => {
        const username = usernameInput.value.trim();
        const password = passwordInput.value.trim();

        if (approvedStudents[username] && approvedStudents[username] === password) {
            errorMessage.style.display = "none";
            loginSection.style.display = "none";
            currentUsername = username;

            if (username === "admin") {
                adminSection.style.display = "block";
                loadAdminData();
            } else {
                // Check Attempt Limit before starting
                const userReport = JSON.parse(localStorage.getItem(`quiz_report_ch5_s5_${currentUsername}`)) || { bestScore: 0, attempts: 0 };
                
                if (userReport.attempts >= attemptLimit) {
                    limitSection.style.display = "block";
                } else {
                    quizSection.style.display = "block";
                    studentNameDisplay.innerText = username;
                    resultStudentName.innerText = username;

                    loadQuestion();
                    startTimer(10 * 60); // 10 Minutes Timer
                }
            }
        } else {
            errorMessage.style.display = "block";
        }
    });

    // --- Admin Dashboard Storage ---
    function loadAdminData() {
        adminTableBody.innerHTML = "";
        Object.keys(approvedStudents).forEach(user => {
            if (user !== "admin") {
                const userReport = JSON.parse(localStorage.getItem(`quiz_report_ch5_s5_${user}`)) || { bestScore: "পরীক্ষা দেয়নি", attempts: 0 };
                
                let statusText = "চলমান";
                let statusColor = "#27ae60";
                if (userReport.attempts >= attemptLimit) {
                    statusText = "লকড (সীমা শেষ)";
                    statusColor = "var(--wrong-color)";
                } else if (userReport.attempts === 0) {
                    statusText = "অংশগ্রহণ করেনি";
                    statusColor = "#7f8c8d";
                }

                const row = document.createElement("tr");
                row.innerHTML = `
                    <td><strong>${user}</strong></td>
                    <td style="color: ${typeof userReport.bestScore === 'number' ? 'var(--primary-color)' : '#7f8c8d'}; font-weight: bold;">
                        ${typeof userReport.bestScore === 'number' ? userReport.bestScore + ' / 15' : userReport.bestScore}
                    </td>
                    <td><span style="background: #e2e8f0; padding: 3px 10px; border-radius: 10px; font-weight: bold;">${userReport.attempts} / ${attemptLimit} বার</span></td>
                    <td style="color: ${statusColor}; font-weight: bold;">${statusText}</td>
                `;
                adminTableBody.appendChild(row);
            }
        });
    }

    function clearReports() {
        if (confirm("আপনি কি নিশ্চিতভাবে সমস্ত ছাত্র-ছাত্রীর পরীক্ষার রেকর্ড ও অ্যাটেম্পট হিস্ট্রি ডিলিট করে লিমিট নতুন করে রিসেট করতে চান?")) {
            Object.keys(approvedStudents).forEach(user => {
                if (user !== "admin") {
                    localStorage.removeItem(`quiz_report_ch5_s5_${user}`);
                }
            });
            loadAdminData();
            alert("সমস্ত ডাটা এবং পরীক্ষার লিমিট সফলভাবে রিসেট করা হয়েছে।");
        }
    }

    // --- Life Science Chapter 5 Set 5 Question Data Bank ---
    const quizData = [
        {
            question: "১. মানব জনসংখ্যা বা পপুলেশন সম্পর্কিত বিজ্ঞানসম্মত অধ্যয়নকে কী বলা হয়?",
            options: ["জেনেটিক্স", "ডেমোগ্রাফি (Demography)", "ইকোসিস্টেম", "জিওগ্রাফি"],
            answer: "ডেমোগ্রাফি (Demography)",
            explanation: "মানুষের জনসংখ্যা, জন্মহার, মৃত্যুহার, বয়স ইত্যাদি পরিসংখ্যান নিয়ে বিজ্ঞানসম্মত আলোচনাকে ডেমোগ্রাফি বলে।"
        },
        {
            question: "২. কোনো পপুলেশনের একক সময়ে যে সংখ্যায় জীবের মৃত্যু ঘটে, তাকে কী বলে?",
            options: ["ন্যাটালিটি", "مর্টালিটি (Mortality) বা মৃত্যুহার", "লিঙ্গ অনুপাত", "জনবিস্ফোরণ"],
            answer: "مর্টালিটি (Mortality) বা মৃত্যুহার",
            explanation: "একক সময়ে পপুলেশনে মৃতের মোট সংখ্যাই হলো মর্টালিটি, যা চিকিৎসা বিজ্ঞানের উন্নতির ফলে বর্তমানে অনেকটা কমেছে।"
        },
        {
            question: "৩. পপুলেশনে প্রজাতির সদস্য সংখ্যা একক সময়ে যে হারে বৃদ্ধি পায়, তাকে কী বলে?",
            options: ["ন্যাটালিটি (Natality) বা জন্মহার", "মর্টালিটি", "মাইগ্রেশন", "ঘনত্ব"],
            answer: "ন্যাটালিটি (Natality) বা জন্মহার",
            explanation: "নির্দিষ্ট সময়ে জন্মানো নতুন সদস্যদের সংখ্যাকে ন্যাটালিটি বা জন্মহার বলে।"
        },
        {
            question: "৪. মানুষের ক্রমবর্ধমান চাহিদার ফলে নিচের কোন অনবীকারী (Non-renewable) প্রাকৃতিক সম্পদটি দ্রুত নিঃশেষ হওয়ার পথে?",
            options: ["সৌরশক্তি", "কয়লা ও খনিজ তেল", "অরণ্য", "মৎস্য সম্পদ"],
            answer: "কয়লা ও খনিজ তেল",
            explanation: "কয়লা, খনিজ তেল এবং প্রাকৃতিক গ্যাস হলো অনবীকারী সম্পদ, যা একবার ব্যবহার করলে আর পূরণ করা সম্ভব নয়।"
        },
        {
            question: "৫. নিচের কোনটি একটি নবীকারী (Renewable) প্রাকৃতিক সম্পদের উদাহরণ?",
            options: ["কয়লা", "পেট্রোলিয়াম", "মৎস্য ও অরণ্য সম্পদ", "প্রাকৃতিক গ্যাস"],
            answer: "মৎস্য ও অরণ্য সম্পদ",
            explanation: "অরণ্য বা মাছ হলো জীবজ সম্পদ যা সুপরিকল্পিতভাবে ব্যবহারের মাধ্যমে পুনরায় উৎপাদন বা নবীকরণ করা সম্ভব।"
        },
        {
            question: "৬. জনসংখ্যা বৃদ্ধির হারের সঙ্গে কোন উপাদানের উৎপাদনের হারের চরম বৈষম্য পৃথিবীতে গভীর সংকট তৈরি করেছে?",
            options: ["খনিজ উৎপাদন", "খাদ্য উৎপাদন", "বস্ত্র উৎপাদন", "যান উৎপাদন"],
            answer: "খাদ্য উৎপাদন",
            explanation: "মানুষের সংখ্যা যে হারে জ্যামিতিক হারে বাড়ছে, সেই হারে কৃষিজমিতে খাদ্য উৎপাদন সম্ভব হচ্ছে না, ফলে বিশ্বজুড়ে খাদ্যাভাব দেখা দিচ্ছে।"
        },
        {
            question: "৭. কৃষিকাজে মাটির তলার জলের যথেচ্ছ ব্যবহারের ফলে বর্তমানে কোন মারাত্মক সমস্যাটি প্রকট হয়ে উঠেছে?",
            options: ["মাটির উর্বরতা বৃদ্ধি", "মিষ্টি জল বা পানীয় জলের অভাব", "নদীর জল বৃদ্ধি", "সমুদ্রের জলস্তর বৃদ্ধি"],
            answer: "মিষ্টি জল বা পানীয় জলের অভাব",
            explanation: "সেচের কাজে ভূগর্ভস্থ জল অতিরিক্ত তোলায় জলের স্তর অনেক নিচে নেমে যাচ্ছে, ফলে গ্রীষ্মকালে নলকূপে জল পাওয়া যায় না।"
        },
        {
            question: "৮. নদীর জলের অধিকার নিয়ে ভবিষ্যৎ পৃথিবীতে এক দেশ থেকে অন্য দেশের মধ্যে কোন সংঘাতের আশঙ্কা করা হচ্ছে?",
            options: ["বিশ্বযুদ্ধ", "জল-যুদ্ধ (Water War)", "বাণিজ্য যুদ্ধ", "শীতল যুদ্ধ"],
            answer: "জল-যুদ্ধ (Water War)",
            explanation: "নদীর বক্ষে এক দেশ বাঁধ নির্মাণ করলে অন্য দেশ জল থেকে বঞ্চিত হয়, যার ফলে জল নিয়ে দেশগুলোর মধ্যে যুদ্ধের পরিবেশ তৈরি হচ্ছে।"
        },
        {
            question: "৯. ক্রমবর্ধমান জনসংখ্যার কারণে বাসস্থান, বিদ্যালয় ও শিল্প প্রতিষ্ঠান নির্মাণের ফলে পরিবেশের কোন অংশটি সবচেয়ে বেশি ধ্বংস হচ্ছে?",
            options: ["মরুভূমি", "সমুদ্র", "অরণ্য ও জলাভূমি", "পাহাড়"],
            answer: "অরণ্য ও জলাভূমি",
            explanation: "মানুষের থাকার জায়গার জন্য নির্বিচারে জঙ্গল কাটা পড়ছে এবং জলাভূমি ভরাট করে ইমারত তৈরি হচ্ছে।"
        },
        {
            question: "১০. বিশ্ব উষ্ণায়ন বা গ্লোবাল ওয়ার্মিংয়ের ফলে সুন্দরবন বা উপকূলবর্তী নিচু এলাকায় কোন মারাত্মক বিপদের হাতছানি দেখা দিচ্ছে?",
            options: ["অতিবৃষ্টি", "বরণ জমা", "সমুদ্রের জলের স্তর বৃদ্ধি ও দ্বীপভূমির নিমজ্জন", "ভূমিকম্প"],
            answer: "সমুদ্রের জলের স্তর বৃদ্ধি ও দ্বীপভূমির নিমজ্জন",
            explanation: "মেরু অঞ্চলের বরফ গলে সমুদ্রের জলস্ফীতি ঘটার কারণে সমুদ্র তীরবর্তী অঞ্চল ও ছোট দ্বীপগুলো জলের তলায় তলিয়ে যাচ্ছে।"
        },
        {
            question: "১১. বায়ুমণ্ডলে ক্লোরোф্লুরো কার্বন (CFC), নাইট্রাস অক্সাইড (N₂O) ইত্যাদির পরিমাণ বাড়ার কারণে কোন স্তরটি ক্ষয়ে যাচ্ছে?",
            options: ["ট্রপোস্ফিয়ার", "স্ট্র্যাটোস্ফিয়ার", "ওজোন স্তর (Ozone layer)", "মেসোস্ফিয়ার"],
            answer: "ওজোন স্তর (Ozone layer)",
            explanation: "এই দূষক গ্যাসগুলো ওজোন স্তরে ছিদ্র তৈরি করছে, ফলে অতিবেগুনি রশ্মি পৃথিবীতে এসে মানুষের ত্বকের ক্যানসার ও চোখে ছানি পড়া বাড়াচ্ছে।"
        },
        {
            question: "১২. নৈসর্গিক প্রাকৃতিক দৃশ্য (যেমন- সুন্দর পাহাড় বা সমুদ্র) কী ধরনের সম্পদের উদাহরণ?",
            options: ["অনবীকারী সম্পদ", "নবীকারী সম্পদ", "অপরিবর্তনীয় প্রাকৃতিক সম্পদ (Unalterable Natural Resources)", "কৃত্রিম সম্পদ"],
            answer: "অপরিবর্তনীয় প্রাকৃতিক সম্পদ (Unalterable Natural Resources)",
            explanation: "যে সম্পদের প্রাচুর্য মানুষ কেবল দৃষ্টির মাধ্যমে উপভোগ করে কিন্তু খরচ করতে বা ব্যবহারে অপারক, তাকে অপরিবর্তনীয় সম্পদ বলে।"
        },
        {
            question: "১৩. জনসংখ্যা বৃদ্ধির একটি অন্যতম প্রধান কারণ কী?",
            options: ["কৃষির ফলন হ্রাস", "মৃত্যুহার হ্রাস পাওয়া (চিকিৎসাবিজ্ঞানের উন্নতির কারণে)", "জন্মহার কমে যাওয়া", "দূষণ বৃদ্ধি"],
            answer: "মৃত্যুহার হ্রাস পাওয়া (চিকিৎসাবিজ্ঞানের উন্নতির কারণে)",
            explanation: "আধুনিক চিকিৎসা, মহামারির টিকা এবং খাদ্য উৎপাদনের উন্নতির ফলে মানুষের আয়ু বেড়েছে এবং মৃত্যুহার অনেক কমে গেছে।"
        },
        {
            question: "১৪. হাঁপানি বা অ্যাজমা রোগীর সংখ্যা দিন দিন এত বেড়ে চলার প্রধান কারণ কী?",
            options: ["মিষ্টি জলের অভাব", "জনসংখ্যা বৃদ্ধি ও কলকারখানা-গাড়ির ধোঁয়ায় বায়ুদূষণ (অ্যালারজেন বৃদ্ধি)", "জলদূষণ", "মাটি দূষণ"],
            answer: "জনসংখ্যা বৃদ্ধি ও কলকারখানা-গাড়ির ধোঁয়ায় বায়ুদূষণ (অ্যালারজেন বৃদ্ধি)",
            explanation: "ধোঁয়া, ধুলো ও পরাগরেণুর মতো প্রাকৃতিক ও কৃত্রিম অ্যালারজেন পরিবেশে বৃদ্ধি পাওয়ায় শ্বাসনালির এই রোগটি মারাত্মক আকার নিয়েছে।"
        },
        {
            question: "১৫. অরণ্য ধ্বংস বা ডিফরেস্টেশনের ফলে কোনটি সরাসরি বিঘ্নিত হয়?",
            options: ["নদীর জল বৃদ্ধি পায়", "বন্যপ্রাণীর অবলুপ্তি ঘটে এবং বাস্তুতন্ত্র বিনষ্ট হয়", "মাটির উর্বরতা বাড়ে", "মাছের সংখ্যা বাড়ে"],
            answer: "বন্যপ্রাণীর অবলুপ্তি ঘটে এবং বাস্তুতন্ত্র বিনষ্ট হয়",
            explanation: "বন জঙ্গল হলো প্রাণীদের বাসস্থান। জঙ্গল ধ্বংস হলে প্রাণীরা মারা যায় এবং পুরো জীববৈচিত্র্য ও বাস্তুতন্ত্র বিপন্ন হয়।"
        }
    ];

    let currentQuestionIndex = 0;
    let score = 0;
    let selectedOption = "";
    let userAnswers = [];
    let timerInterval;

    const questionTextEl = document.getElementById("question-text");
    const optionsListEl = document.getElementById("options-list");
    const nextBtn = document.getElementById("next-btn");
    const qCounterEl = document.getElementById("q-counter");
    const timerDisplayEl = document.getElementById("timer-display");

    const resultSection = document.getElementById("result-section");
    const reviewContainer = document.getElementById("review-container");
    const finalScoreEl = document.getElementById("final-score");

    function startTimer(durationInSeconds) {
        let timeRemaining = durationInSeconds;
        
        timerInterval = setInterval(() => {
            let minutes = Math.floor(timeRemaining / 60);
            let seconds = timeRemaining % 60;

            minutes = minutes < 10 ? "0" + minutes : minutes;
            seconds = seconds < 10 ? "0" + seconds : seconds;

            timerDisplayEl.innerText = `${minutes}:${seconds}`;

            if (timeRemaining <= 0) {
                clearInterval(timerInterval);
                alert("আপনার কুইজের নির্ধারিত ১০ মিনিট সময় শেষ হয়ে গেছে! কুইজটি স্বয়ংক্রিয়ভাবে সাবমিট করা হচ্ছে।");
                showResults();
            }
            timeRemaining--;
        }, 1000);
    }

    function loadQuestion() {
        selectedOption = "";
        const currentData = quizData[currentQuestionIndex];

        qCounterEl.innerText = `প্রশ্ন: ${currentQuestionIndex + 1} / ${quizData.length}`;
        questionTextEl.innerText = currentData.question;
        optionsListEl.innerHTML = "";

        if(currentQuestionIndex === quizData.length - 1) {
            nextBtn.innerText = "কুইজ সম্পূর্ণ সাবমিট করুন";
            nextBtn.style.backgroundColor = "#27ae60";
        } else {
            nextBtn.innerText = "পরবর্তী প্রশ্ন";
            nextBtn.style.backgroundColor = "var(--primary-color)";
        }

        currentData.options.forEach(option => {
            const li = document.createElement("li");
            li.classList.add("option-item");
            li.innerText = option;
            li.onclick = () => selectOption(li, option);
            optionsListEl.appendChild(li);
        });
    }

    function selectOption(li, option) {
        const allOptions = document.querySelectorAll(".option-item");
        allOptions.forEach(opt => opt.classList.remove("selected"));
        li.classList.add("selected");
        selectedOption = option;
    }

    function saveStudentReport(finalScore) {
        let userReport = JSON.parse(localStorage.getItem(`quiz_report_ch5_s5_${currentUsername}`)) || { bestScore: 0, attempts: 0 };
        
        userReport.attempts += 1; 
        if (finalScore > userReport.bestScore) {
            userReport.bestScore = finalScore; 
        }

        localStorage.setItem(`quiz_report_ch5_s5_${currentUsername}`, JSON.stringify(userReport));
    }

    function showResults() {
        clearInterval(timerInterval);
        quizSection.style.display = "none";
        resultSection.style.display = "block";
        finalScoreEl.innerText = `স্কোর: ${score} / ${quizData.length}`;

        saveStudentReport(score);

        reviewContainer.innerHTML = ""; 
        quizData.forEach((item, index) => {
            const userAnswer = userAnswers[index];
            const isCorrect = userAnswer === item.answer;

            const reviewHtml = `
                <div class="review-item">
                    <div class="review-q">${item.question}</div>
                    <div class="review-ans">
                        আপনার উত্তর: <span class="${isCorrect ? 'ans-correct' : 'ans-wrong'}">
                            ${userAnswer ? userAnswer : 'উত্তর দেননি (Skipped/Time Out)'}
                        </span>
                    </div>
                    ${!isCorrect ? `<div class="review-ans">সঠিক উত্তর: <span class="ans-correct">${item.answer}</span></div>` : ''}
                    <div class="explanation">
                        <strong>ব্যাখ্যা:</strong> ${item.explanation}
                    </div>
                </div>
            `;
            reviewContainer.innerHTML += reviewHtml;
        });
    }

    nextBtn.addEventListener("click", () => {
        if (selectedOption === "") {
            const confirmSkip = confirm("আপনি কোনো অপশন সিলেক্ট করেননি। আপনি কি এই প্রশ্নটি স্কিপ (Skip) করতে চান?");
            if (!confirmSkip) {
                return; 
            }
            userAnswers[currentQuestionIndex] = null; 
        } else {
            userAnswers[currentQuestionIndex] = selectedOption;
            if (selectedOption === quizData[currentQuestionIndex].answer) {
                score++;
            }
        }

        currentQuestionIndex++;

        if (currentQuestionIndex < quizData.length) {
            loadQuestion();
        } else {
            showResults();
        }
    });
</script>

</body>
</html>
