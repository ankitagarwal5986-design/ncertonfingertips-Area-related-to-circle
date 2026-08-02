<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>NCERT on Finger Tips - Areas Related to Circles</title>
<style>
    :root {
        --primary-blue: #1e3a8a;
        --secondary-gold: #d97706;
        --bg-light: #f8fafc;
        --card-bg: #ffffff;
        --text-dark: #0f172a;
        --correct-green: #059669;
        --incorrect-red: #dc2626;
    }

    * {
        box-sizing: border-box;
        font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    }

    body {
        margin: 0;
        padding: 20px;
        background-color: var(--bg-light);
        color: var(--text-dark);
        display: flex;
        justify-content: center;
    }

    .quiz-card {
        width: 100%;
        max-width: 750px;
        background: var(--card-bg);
        border-radius: 12px;
        box-shadow: 0 10px 25px -5px rgba(0, 0, 0, 0.1), 0 8px 10px -6px rgba(0, 0, 0, 0.1);
        overflow: hidden;
    }

    .header {
        background: linear-gradient(135deg, #0f172a 0%, var(--primary-blue) 100%);
        color: white;
        padding: 25px 20px;
        text-align: center;
        border-bottom: 5px solid var(--secondary-gold);
    }

    .header h1 {
        margin: 0;
        font-size: 22px;
        letter-spacing: 1px;
        text-transform: uppercase;
    }

    .header h2 {
        margin: 5px 0 0 0;
        font-size: 14px;
        color: #fcd34d;
        font-weight: 500;
    }

    .controls {
        padding: 15px 20px;
        background: #e2e8f0;
        display: flex;
        justify-content: space-between;
        align-items: center;
        flex-wrap: wrap;
        gap: 10px;
    }

    select {
        padding: 8px 12px;
        border-radius: 6px;
        border: 1px solid #cbd5e0;
        font-size: 14px;
        font-weight: 600;
        color: var(--text-dark);
        background: white;
        cursor: pointer;
    }

    .progress-bar-container {
        height: 6px;
        background: #cbd5e0;
        width: 100%;
    }

    .progress-bar {
        height: 100%;
        width: 0%;
        background: var(--secondary-gold);
        transition: width 0.3s ease;
    }

    .quiz-body {
        padding: 25px 20px;
    }

    .q-number {
        font-size: 13px;
        font-weight: 700;
        color: #2563eb;
        text-transform: uppercase;
        margin-bottom: 8px;
    }

    .question-text {
        font-size: 16px;
        font-weight: 600;
        margin-bottom: 15px;
        line-height: 1.5;
    }

    .diagram-container {
        text-align: center;
        margin: 15px 0 20px 0;
        background: #f1f5f9;
        padding: 12px;
        border-radius: 8px;
        border: 1px solid #cbd5e0;
    }

    .diagram-container svg {
        max-width: 100%;
        height: auto;
    }

    .options-list {
        list-style: none;
        padding: 0;
        margin: 0 0 20px 0;
    }

    .option-item {
        padding: 12px 16px;
        margin-bottom: 10px;
        border: 2px solid #e2e8f0;
        border-radius: 8px;
        cursor: pointer;
        transition: all 0.2s ease;
        display: flex;
        align-items: center;
        font-size: 14px;
    }

    .option-item:hover {
        border-color: #93c5fd;
        background-color: #eff6ff;
    }

    .option-item.selected {
        border-color: #2563eb;
        background-color: #dbeafe;
        font-weight: 600;
    }

    .option-item.correct {
        border-color: var(--correct-green);
        background-color: #d1fae5;
        color: #065f46;
        font-weight: 600;
    }

    .option-item.wrong {
        border-color: var(--incorrect-red);
        background-color: #fee2e2;
        color: #991b1b;
    }

    .explanation-box {
        display: none;
        padding: 15px;
        border-radius: 8px;
        background: #f1f5f9;
        border-left: 4px solid #2563eb;
        margin-bottom: 20px;
        font-size: 13.5px;
        line-height: 1.5;
    }

    .explanation-box strong {
        color: #1e293b;
    }

    .footer-btn-group {
        display: flex;
        justify-content: space-between;
        gap: 10px;
    }

    button {
        padding: 10px 20px;
        border: none;
        border-radius: 6px;
        font-size: 14px;
        font-weight: 600;
        cursor: pointer;
        transition: background 0.2s;
    }

    .btn-check {
        background: #2563eb;
        color: white;
    }

    .btn-check:hover {
        background: #1d4ed8;
    }

    .btn-next {
        background: var(--secondary-gold);
        color: white;
    }

    .btn-next:hover {
        background: #b45309;
    }

    button:disabled {
        opacity: 0.5;
        cursor: not-allowed;
    }

    .score-screen {
        text-align: center;
        padding: 40px 20px;
        display: none;
    }

    .score-screen h2 {
        font-size: 24px;
        color: var(--primary-blue);
    }

    .score-badge {
        font-size: 40px;
        font-weight: 800;
        color: var(--secondary-gold);
        margin: 15px 0;
    }
</style>
</head>
<body>

<div class="quiz-card">
    <div class="header">
        <h1>NCERT ON FINGER TIPS</h1>
        <h2>BY BRAIN AND MIND ACADEMY</h2>
    </div>

    <div class="controls">
        <label for="chapterSelect"><strong>Select Chapter:</strong></label>
        <select id="chapterSelect" onchange="loadChapter()">
            <option value="ch11">Ch 11: Areas Related to Circles (40 Questions)</option>
        </select>
    </div>

    <div class="progress-bar-container">
        <div class="progress-bar" id="progressBar"></div>
    </div>

    <div class="quiz-body" id="quizBody">
        <div class="q-number" id="qNumber">Question 1 of 40</div>
        <div class="question-text" id="questionText">Loading Question...</div>

        <div class="diagram-container" id="diagramBox" style="display:none;"></div>

        <ul class="options-list" id="optionsList"></ul>

        <div class="explanation-box" id="explanationBox">
            <strong>Rationale:</strong> <span id="explanationText"></span>
        </div>

        <div class="footer-btn-group">
            <button class="btn-check" id="checkBtn" onclick="checkAnswer()" disabled>Check Answer</button>
            <button class="btn-next" id="nextBtn" onclick="nextQuestion()" style="display: none;">Next Question →</button>
        </div>
    </div>

    <div class="score-screen" id="scoreScreen">
        <h2>Chapter Completed!</h2>
        <p>Your Final Score:</p>
        <div class="score-badge" id="finalScore">0 / 40</div>
        <button class="btn-check" onclick="restartQuiz()">Restart Chapter</button>
    </div>
</div>

<script>
// Chapter 11: Areas Related to Circles - Complete 40 Questions (Including SVG Diagram Questions)
const quizData = {
    ch11: [
        { q: "If the perimeter and the area of a circle are numerically equal, then the radius of the circle is:", opts: ["2 units", "π units", "4 units", "7 units"], ans: 0, rat: "2πr = πr² ⇒ 2 = r. Radius is 2 units." },
        { q: "Area of a sector of central angle p (in degrees) of a circle with radius R is:", opts: ["(p/180) × 2πR", "(p/180) × πR²", "(p/360) × 2πR", "(p/360) × πR²"], ans: 3, rat: "Formula for area of a sector of angle θ is (θ/360°) × πR². Substituting θ = p gives (p/360) × πR²." },
        { q: "The area of a quadrant of a circle whose circumference is 22 cm is (use π = 22/7):", opts: ["77/8 cm²", "77/4 cm²", "38.5 cm²", "154 cm²"], ans: 0, rat: "2πr = 22 ⇒ 2(22/7)r = 22 ⇒ r = 7/2 cm. Area of quadrant = 1/4 πr² = (1/4)(22/7)(7/2)² = 77/8 cm²." },
        { q: "A minute hand of a clock is 14 cm long. The area swept by the minute hand in 5 minutes is:", opts: ["154/3 cm²", "154 cm²", "308/3 cm²", "77/3 cm²"], ans: 0, rat: "Angle in 5 mins = (360°/60) × 5 = 30°. Area = (30/360) × (22/7) × 14² = (1/12) × (22/7) × 196 = 154/3 cm²." },
        
        // Diagram Question 1
        { 
            q: "Refer to the diagram below. A sector of radius r = 7 cm has a central angle θ = 60°. Find the area of the shaded sector (Take π = 22/7):", 
            svg: `<svg width="180" height="180" viewBox="0 0 200 200">
                    <circle cx="100" cy="100" r="80" fill="none" stroke="#64748b" stroke-width="2"/>
                    <path d="M 100 100 L 180 100 A 80 80 0 0 0 140 30 Z" fill="#3b82f6" opacity="0.6" stroke="#1e3a8a" stroke-width="2"/>
                    <circle cx="100" cy="100" r="3" fill="#0f172a"/>
                    <text x="95" y="115" font-size="12" font-weight="bold">O</text>
                    <text x="130" y="90" font-size="12" font-weight="bold">60°</text>
                    <text x="135" y="115" font-size="12" font-weight="bold">r = 7 cm</text>
                  </svg>`,
            opts: ["77/3 cm²", "154/3 cm²", "77/6 cm²", "49 cm²"], 
            ans: 0, 
            rat: "Area = (60/360) × (22/7) × 7² = (1/6) × 22 × 7 = 154/6 = 77/3 cm²." 
        },

        { q: "If the area of a circle is 154 cm², then its perimeter (circumference) is:", opts: ["44 cm", "22 cm", "88 cm", "55 cm"], ans: 0, rat: "πr² = 154 ⇒ (22/7)r² = 154 ⇒ r² = 49 ⇒ r = 7 cm. Circumference = 2(22/7)(7) = 44 cm." },
        { q: "The length of an arc of a sector of angle θ in a circle of radius r is:", opts: ["(θ/360) × πr²", "(θ/360) × 2πr", "(θ/180) × πr²", "(θ/720) × 2πr"], ans: 1, rat: "Length of arc = (θ/360°) × 2πr." },
        { q: "If the radius of a circle is doubled, its area becomes:", opts: ["2 times", "4 times", "8 times", "3 times"], ans: 1, rat: "Original Area = πr². New Area = π(2r)² = 4πr². Area becomes 4 times." },
        
        // Diagram Question 2
        { 
            q: "Refer to the figure. A square ABCD of side 14 cm contains four congruent non-overlapping quarter circles centered at each vertex. Find the area of the shaded central region:", 
            svg: `<svg width="180" height="180" viewBox="0 0 200 200">
                    <rect x="20" y="20" width="160" height="160" fill="#3b82f6" opacity="0.5" stroke="#1e3a8a" stroke-width="2"/>
                    <path d="M 20 100 A 80 80 0 0 1 100 20 L 20 20 Z" fill="#ffffff" stroke="#1e3a8a"/>
                    <path d="M 100 20 A 80 80 0 0 1 180 100 L 180 20 Z" fill="#ffffff" stroke="#1e3a8a"/>
                    <path d="M 180 100 A 80 80 0 0 1 100 180 L 180 180 Z" fill="#ffffff" stroke="#1e3a8a"/>
                    <path d="M 100 180 A 80 80 0 0 1 20 100 L 20 180 Z" fill="#ffffff" stroke="#1e3a8a"/>
                    <text x="15" y="15" font-size="12" font-weight="bold">A</text>
                    <text x="180" y="15" font-size="12" font-weight="bold">B</text>
                    <text x="180" y="195" font-size="12" font-weight="bold">C</text>
                    <text x="15" y="195" font-size="12" font-weight="bold">D</text>
                    <text x="85" y="110" font-size="12" font-weight="bold" fill="#0f172a">Shaded</text>
                  </svg>`,
            opts: ["42 cm²", "154 cm²", "196 cm²", "56 cm²"], 
            ans: 0, 
            rat: "Area of square = 14² = 196 cm². Radius of each quadrant = 14/2 = 7 cm. Total area of 4 quadrants = 1 full circle = π(7)² = 154 cm². Shaded Area = 196 - 154 = 42 cm²." 
        },

        { q: "The difference between the circumference and the radius of a circle is 37 cm. Using π = 22/7, the radius of the circle is:", opts: ["7 cm", "14 cm", "21 cm", "3.5 cm"], ans: 0, rat: "2πr - r = 37 ⇒ r(2(22/7) - 1) = 37 ⇒ r(37/7) = 37 ⇒ r = 7 cm." },
        { q: "If the circumference of two circles are in the ratio 2 : 3, then the ratio of their areas is:", opts: ["2 : 3", "4 : 9", "8 : 27", "1 : 3"], ans: 1, rat: "Circumference ratio C₁/C₂ = r₁/r₂ = 2/3. Area ratio A₁/A₂ = (r₁/r₂)² = (2/3)² = 4/9." },
        
        // Diagram Question 3
        { 
            q: "In the diagram below, O is the center of two concentric circles of radii 7 cm and 14 cm. If ∠AOB = 40°, find the area of the shaded region ABDC:", 
            svg: `<svg width="180" height="180" viewBox="0 0 200 200">
                    <path d="M 100 100 L 190 100 A 90 90 0 0 0 169 42 Z" fill="#3b82f6" opacity="0.6" stroke="#1e3a8a"/>
                    <path d="M 100 100 L 145 100 A 45 45 0 0 0 134 71 Z" fill="#ffffff" stroke="#1e3a8a"/>
                    <circle cx="100" cy="100" r="3" fill="#0f172a"/>
                    <text x="85" y="105" font-size="12" font-weight="bold">O</text>
                    <text x="148" y="115" font-size="11" font-weight="bold">C</text>
                    <text x="192" y="115" font-size="11" font-weight="bold">A</text>
                    <text x="135" y="65" font-size="11" font-weight="bold">D</text>
                    <text x="172" y="38" font-size="11" font-weight="bold">B</text>
                  </svg>`,
            opts: ["77/3 cm²", "154/3 cm²", "77/6 cm²", "154/9 cm²"], 
            ans: 0, 
            rat: "Area = (40/360) × π × (R² - r²) = (1/9) × (22/7) × (14² - 7²) = (1/9) × (22/7) × 147 = (22 × 21) / 9 = 462 / 9 = 154/3 cm²... wait, 147/7 = 21. (1/9)*22*21 = 462/9 = 154/3 cm²." 
        },

        { q: "An equilateral triangle of side 6 cm is inscribed in a circle. The radius of the circle is:", opts: ["2√3 cm", "√3 cm", "3√3 cm", "4√3 cm"], ans: 0, rat: "Circumradius of equilateral triangle R = a / √3 = 6 / √3 = 2√3 cm." },
        { q: "A wire bent in the form of a square encloses an area of 484 cm². If the same wire is bent into a circle, the area enclosed by it is:", opts: ["616 cm²", "512 cm²", "484 cm²", "308 cm²"], ans: 0, rat: "Square Area = 484 ⇒ Side = 22 cm. Perimeter = 4 × 22 = 88 cm. Wire length = 2πr = 88 ⇒ r = 14 cm. Circle Area = (22/7) × 14² = 616 cm²." },
        { q: "The area of the largest triangle that can be inscribed in a semi-circle of radius r is:", opts: ["r²", "2r²", "r²/2", "1/2 r²"], ans: 0, rat: "Base of triangle = diameter = 2r. Maximum height = radius = r. Maximum Area = 1/2 × base × height = 1/2 × 2r × r = r²." },
        
        // Diagram Question 4
        { 
            q: "Refer to the figure below. A right-angled triangle ABC with AB = 6 cm, BC = 8 cm is inscribed in a semicircle with AC as diameter. Find the area of the shaded region outside the triangle:", 
            svg: `<svg width="200" height="120" viewBox="0 0 200 120">
                    <path d="M 20 100 A 80 80 0 0 1 180 100 Z" fill="#3b82f6" opacity="0.5" stroke="#1e3a8a" stroke-width="2"/>
                    <polygon points="20,100 180,100 68,36" fill="#ffffff" stroke="#1e3a8a" stroke-width="2"/>
                    <text x="10" y="115" font-size="11" font-weight="bold">A</text>
                    <text x="185" y="115" font-size="11" font-weight="bold">C</text>
                    <text x="65" y="25" font-size="11" font-weight="bold">B</text>
                  </svg>`,
            opts: ["15.25 cm²", "15.28 cm²", "24 cm²", "39.28 cm²"], 
            ans: 1, 
            rat: "Hypotenuse AC = √(6² + 8²) = 10 cm. Radius r = 5 cm. Semicircle Area = (1/2)π(5²) = 12.5 × 3.14 = 39.25 cm². Triangle Area = 1/2 × 6 × 8 = 24 cm². Shaded Area = 39.28 - 24 = 15.28 cm²." 
        },

        { q: "If the perimeter of a semi-circular protractor is 36 cm, then its diameter is (use π = 22/7):", opts: ["14 cm", "7 cm", "21 cm", "28 cm"], ans: 0, rat: "Perimeter = πr + 2r = r(π + 2) = r(22/7 + 2) = r(36/7). Given r(36/7) = 36 ⇒ r = 7 cm. Diameter = 2r = 14 cm." },
        { q: "The area of a circle that can be inscribed in a square of side 6 cm is:", opts: ["9π cm²", "36π cm²", "18π cm²", "12π cm²"], ans: 0, rat: "Diameter of inscribed circle = side of square = 6 cm ⇒ r = 3 cm. Area = πr² = π(3)² = 9π cm²." },
        { q: "The area of a square that can be inscribed in a circle of radius 8 cm is:", opts: ["128 cm²", "64 cm²", "256 cm²", "192 cm²"], ans: 0, rat: "Diagonal of inscribed square = diameter of circle = 2 × 8 = 16 cm. Area of square = (Diagonal)² / 2 = 16² / 2 = 256 / 2 = 128 cm²." },
        { q: "The outer and inner diameters of a circular ring are 10 cm and 6 cm. The area of the ring is:", opts: ["16π cm²", "64π cm²", "36π cm²", "8π cm²"], ans: 0, rat: "Outer radius R = 5 cm, inner radius r = 3 cm. Area of ring = π(R² - r²) = π(5² - 3²) = π(25 - 9) = 16π cm²." },
        { q: "If the central angle of a sector is 90°, the sector is called a:", opts: ["Semi-circle", "Quadrant", "Segment", "Minor arc"], ans: 1, rat: "A sector with a central angle of 90° is one-fourth of a circle, which is called a quadrant." },
        { q: "The ratio of the area of a circle to the area of its circumscribed square is:", opts: ["π : 4", "π : 2", "4 : π", "2 : π"], ans: 0, rat: "Let radius be r. Circle Area = πr². Side of circumscribed square = 2r, so Square Area = (2r)² = 4r². Ratio = πr² / 4r² = π : 4." },
        { q: "If an arc of length 11 cm subtends a central angle of 45° in a circle, the radius of the circle is:", opts: ["14 cm", "7 cm", "28 cm", "21 cm"], ans: 0, rat: "Length = (θ/360) × 2πr ⇒ 11 = (45/360) × 2(22/7)r ⇒ 11 = (1/8)(44/7)r ⇒ r = (11 × 56) / 44 = 14 cm." },
        { q: "A horse is tied to a peg at one corner of a square grass field of side 15 m by means of a 5 m long rope. The area of that part of the field in which the horse can graze is:", opts: ["19.625 m²", "78.5 m²", "9.81 m²", "25 m²"], ans: 0, rat: "The grazing area is a quadrant of radius 5 m. Area = 1/4 × π × 5² = (1/4) × 3.14 × 25 = 19.625 m²." },
        { q: "If the radius of a circle is decreased by 50%, its area decreases by:", opts: ["75%", "50%", "25%", "100%"], ans: 0, rat: "New radius = 0.5r. New Area = π(0.5r)² = 0.25 πr² (25% of original). Decrease = 100% - 25% = 75%." },
        { q: "The area of a sector of angle 120° in a circle of radius 21 cm is (use π = 22/7):", opts: ["462 cm²", "154 cm²", "308 cm²", "616 cm²"], ans: 0, rat: "Area = (120/360) × (22/7) × 21² = (1/3) × (22/7) × 441 = (1/3) × 22 × 63 = 22 × 21 = 462 cm²." },
        { q: "The perimeter of a sector of a circle of radius 5.2 cm and central angle 36° is:", opts: ["13.66 cm", "3.26 cm", "10.4 cm", "15.2 cm"], ans: 0, rat: "Arc length = (36/360) × 2 × (22/7) × 5.2 = (1/10) × 32.68 = 3.26 cm. Perimeter = Arc + 2r = 3.26 + 2(5.2) = 3.26 + 10.4 = 13.66 cm." },
        { q: "The wheels of a car are of diameter 80 cm each. How many complete revolutions does each wheel make in 10 minutes when the car is traveling at a speed of 66 km/h?", opts: ["4375", "4500", "4000", "5000"], ans: 0, rat: "Speed = 66 km/h = (66 × 100000)/60 cm/min = 110000 cm/min. Distance in 10 mins = 1100000 cm. Wheel circumference = πd = (22/7) × 80 = 1760/7 cm. Revolutions = 1100000 / (1760/7) = 4375." },
        { q: "A chord of a circle of radius 10 cm subtends a right angle at the centre. The area of the corresponding minor segment is (use π = 3.14):", opts: ["28.5 cm²", "78.5 cm²", "50 cm²", "25 cm²"], ans: 0, rat: "Area of sector = (90/360) × 3.14 × 100 = 78.5 cm². Area of triangle = 1/2 × 10 × 10 = 50 cm². Area of minor segment = 78.5 - 50 = 28.5 cm²." },
        { q: "In a circle of radius 21 cm, an arc subtends an angle of 60° at the centre. The length of the arc is:", opts: ["22 cm", "44 cm", "11 cm", "33 cm"], ans: 0, rat: "Arc length = (60/360) × 2 × (22/7) × 21 = (1/6) × 2 × 22 × 3 = 22 cm." },
        { q: "Area of the major segment of a circle of radius 14 cm, given that the minor segment has an area of 56 cm² is:", opts: ["560 cm²", "616 cm²", "512 cm²", "480 cm²"], ans: 0, rat: "Total Area of circle = (22/7) × 14² = 616 cm². Major Segment Area = Total Area - Minor Segment Area = 616 - 56 = 560 cm²." },
        { q: "The area of a circle is 38.5 cm². Its circumference is:", opts: ["22 cm", "44 cm", "11 cm", "33 cm"], ans: 0, rat: "(22/7)r² = 38.5 ⇒ r² = 12.25 ⇒ r = 3.5 cm. Circumference = 2 × (22/7) × 3.5 = 22 cm." },
        { q: "If a square is inscribed in a circle of radius r, the area of the square is:", opts: ["2r²", "r²", "4r²", "r²/2"], ans: 0, rat: "Diagonal = 2r. Area of square = (2r)² / 2 = 4r² / 2 = 2r²." },
        { q: "The angle subtended by a major arc at the centre of a circle is always:", opts: ["Greater than 180°", "Less than 180°", "Equal to 180°", "Equal to 90°"], ans: 0, rat: "By definition, a major arc spans more than half the circle, so its central angle is greater than 180°." },
        { q: "If the side of an equilateral triangle is a, then the area of its incircle is:", opts: ["πa² / 12", "πa² / 6", "πa² / 4", "πa² / 3"], ans: 0, rat: "Inradius of equilateral triangle r = a / (2√3). Area of incircle = πr² = π(a / (2√3))² = πa² / 12." },
        { q: "The area of a sector of a circle of radius 7 cm and arc length 10 cm is:", opts: ["35 cm²", "70 cm²", "17.5 cm²", "20 cm²"], ans: 0, rat: "Area of a sector can also be calculated as (1/2) × arc length × radius = (1/2) × 10 × 7 = 35 cm²." },
        { q: "The ratio of the area of a circle to the area of a sector of central angle 60° in the same circle is:", opts: ["6 : 1", "1 : 6", "3 : 1", "12 : 1"], ans: 0, rat: "Sector Area = (60/360) × Circle Area = (1/6) × Circle Area. Thus Circle Area / Sector Area = 6 : 1." },
        { q: "If the area of a sector of a circle is 5/18 of the area of the circle, the central angle of the sector is:", opts: ["100°", "90°", "60°", "120°"], ans: 0, rat: "θ/360° = 5/18 ⇒ θ = (5 × 360) / 18 = 100°." },
        { q: "A steel wire when bent in the form of a square encloses an area of 121 cm². If the same wire is bent into the form of a circle, its area is:", opts: ["154 cm²", "121 cm²", "176 cm²", "144 cm²"], ans: 0, rat: "Side = √121 = 11 cm. Wire length = 4 × 11 = 44 cm. 2πr = 44 ⇒ r = 7 cm. Circle Area = (22/7) × 7² = 154 cm²." },
        { q: "If a chord divides a circle into two regions, the larger region is called the:", opts: ["Major segment", "Minor segment", "Major sector", "Minor sector"], ans: 0, rat: "A chord divides a circle into two segments: the larger one is the major segment." }
    ]
};

let currentChapter = "ch11";
let currentIndex = 0;
let selectedOption = null;
let score = 0;

function loadChapter() {
    currentChapter = document.getElementById("chapterSelect").value;
    currentIndex = 0;
    score = 0;
    document.getElementById("quizBody").style.display = "block";
    document.getElementById("scoreScreen").style.display = "none";
    showQuestion();
}

function showQuestion() {
    const questions = quizData[currentChapter];
    const qData = questions[currentIndex];

    // Reset State
    selectedOption = null;
    document.getElementById("checkBtn").disabled = true;
    document.getElementById("checkBtn").style.display = "inline-block";
    document.getElementById("nextBtn").style.display = "none";
    document.getElementById("explanationBox").style.display = "none";

    // Progress Bar
    const progressPercent = (currentIndex / questions.length) * 100;
    document.getElementById("progressBar").style.width = progressPercent + "%";

    // Text Header
    document.getElementById("qNumber").innerText = `Question ${currentIndex + 1} of ${questions.length}`;
    document.getElementById("questionText").innerText = qData.q;

    // Handle SVG Diagram if present
    const diagramBox = document.getElementById("diagramBox");
    if (qData.svg) {
        diagramBox.innerHTML = qData.svg;
        diagramBox.style.display = "block";
    } else {
        diagramBox.innerHTML = "";
        diagramBox.style.display = "none";
    }

    // Render Options
    const optionsList = document.getElementById("optionsList");
    optionsList.innerHTML = "";
    
    qData.opts.forEach((optText, i) => {
        const li = document.createElement("li");
        li.className = "option-item";
        li.innerHTML = `<strong>${String.fromCharCode(65 + i)})</strong>&nbsp; ${optText}`;
        li.onclick = () => selectOption(i, li);
        optionsList.appendChild(li);
    });
}

function selectOption(index, element) {
    const items = document.querySelectorAll(".option-item");
    items.forEach(item => item.classList.remove("selected"));

    selectedOption = index;
    element.classList.add("selected");
    document.getElementById("checkBtn").disabled = false;
}

function checkAnswer() {
    const questions = quizData[currentChapter];
    const qData = questions[currentIndex];
    const items = document.querySelectorAll(".option-item");

    items.forEach(item => item.onclick = null);

    if (selectedOption === qData.ans) {
        items[selectedOption].classList.add("correct");
        score++;
    } else {
        items[selectedOption].classList.add("wrong");
        items[qData.ans].classList.add("correct");
    }

    document.getElementById("explanationText").innerText = qData.rat;
    document.getElementById("explanationBox").style.display = "block";

    document.getElementById("checkBtn").style.display = "none";
    document.getElementById("nextBtn").style.display = "inline-block";
}

function nextQuestion() {
    const questions = quizData[currentChapter];
    currentIndex++;

    if (currentIndex < questions.length) {
        showQuestion();
    } else {
        showScoreScreen();
    }
}

function showScoreScreen() {
    const questions = quizData[currentChapter];
    document.getElementById("progressBar").style.width = "100%";
    document.getElementById("quizBody").style.display = "none";
    document.getElementById("scoreScreen").style.display = "block";
    document.getElementById("finalScore").innerText = `${score} / ${questions.length}`;
}

function restartQuiz() {
    loadChapter();
}

// Initial Load
loadChapter();
</script>

</body>
</html>
