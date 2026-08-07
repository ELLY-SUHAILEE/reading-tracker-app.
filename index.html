<!DOCTYPE html>
<html lang="ms">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Reading Tracker Quiz</title>
  <style>
    :root {
      --primary: #4f46e5;
      --primary-hover: #4338ca;
      --bg: #f3f4f6;
      --card-bg: #ffffff;
      --text: #1f2937;
    }

    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background-color: var(--bg);
      color: var(--text);
      margin: 0;
      padding: 20px;
      display: flex;
      justify-content: center;
    }

    .container {
      width: 100%;
      max-width: 800px;
      background: var(--card-bg);
      padding: 25px;
      border-radius: 12px;
      box-shadow: 0 4px 6px -1px rgba(0,0,0,0.1), 0 2px 4px -1px rgba(0,0,0,0.06);
    }

    h1, h2 {
      text-align: center;
      color: var(--primary);
    }

    .form-group {
      margin-bottom: 15px;
    }

    label {
      display: block;
      margin-bottom: 5px;
      font-weight: bold;
    }

    input, select, button {
      width: 100%;
      padding: 10px;
      border-radius: 6px;
      border: 1px solid #ccc;
      box-sizing: border-box;
      font-size: 16px;
    }

    button {
      background-color: var(--primary);
      color: white;
      border: none;
      font-weight: bold;
      cursor: pointer;
      margin-top: 10px;
      transition: background-color 0.2s;
    }

    button:hover {
      background-color: var(--primary-hover);
    }

    .quiz-section, .result-section {
      display: none;
    }

    .question-card {
      background: #fafafa;
      border: 1px solid #e5e7eb;
      border-radius: 8px;
      padding: 15px;
      margin-bottom: 20px;
    }

    .question-title {
      font-size: 18px;
      font-weight: 600;
      margin-bottom: 10px;
    }

    .options-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
      gap: 10px;
      margin-top: 10px;
    }

    .option-card {
      border: 2px solid #e5e7eb;
      border-radius: 8px;
      padding: 12px;
      text-align: center;
      cursor: pointer;
      transition: all 0.2s;
      background: #fff;
    }

    .option-card:hover {
      border-color: var(--primary);
    }

    .option-card.selected {
      border-color: var(--primary);
      background-color: #eeeffe;
    }

    .header-info {
      display: flex;
      justify-content: space-between;
      align-items: center;
      background: #eef2ff;
      padding: 10px 15px;
      border-radius: 6px;
      margin-bottom: 20px;
      font-weight: bold;
      flex-wrap: wrap;
      gap: 10px;
    }

    .status-msg {
      text-align: center;
      margin-top: 15px;
      font-weight: bold;
    }
  </style>
</head>
<body>

<div class="container">
  <!-- BAHAGIAN 1: BORANG PENDAFTARAN -->
  <div id="start-section">
    <h1>Reading Tracker Quiz</h1>
    <div class="form-group">
      <label for="studentName">Nama Murid:</label>
      <input type="text" id="studentName" placeholder="Masukkan nama penuh anda" required>
    </div>
    <div class="form-group">
      <label for="studentClass">Kelas:</label>
      <input type="text" id="studentClass" placeholder="Contoh: 1 Cemerlang" required>
    </div>
    <div class="form-group">
      <label for="setSelect">Pilih Set Soalan:</label>
      <select id="setSelect">
        <!-- Generasi 1 hingga 23 -->
      </select>
    </div>
    <button onclick="startQuiz()">Mula Kuiz</button>
  </div>

  <!-- BAHAGIAN 2: KUIZ -->
  <div id="quiz-section" class="quiz-section">
    <div class="header-info">
      <span id="displayStudent"></span>
      <span id="displayClass"></span>
      <span id="displaySet"></span>
      <span id="displayTimer">Masa: 00:00</span>
    </div>

    <form id="quizForm">
      <div id="questionsContainer"></div>
      <button type="button" onclick="submitQuiz()">Hantar Jawapan</button>
    </form>
  </div>

  <!-- BAHAGIAN 3: KEPUTUSAN -->
  <div id="result-section" class="result-section">
    <h2>Keputusan Kuiz</h2>
    <div class="question-card" style="text-align: center;">
      <p id="resultText" style="font-size: 20px; font-weight: bold;"></p>
      <p id="resultTime"></p>
      <p id="statusMsg" class="status-msg"></p>
    </div>
    <button onclick="location.reload()">Jawab Set Lain</button>
  </div>
</div>

<script>
  const GOOGLE_SCRIPT_URL = "https://script.google.com/macros/s/AKfycbwLzoVdSRVJDOu_ESkWxAE-I23Sorhy4JOvqZSMKW7WOKkYejGe7YEhv3cj4QZEOvNa/exec";

  let rawData = [];
  let currentQuestions = [];
  let userAnswers = {};
  let timerInterval;
  let secondsElapsed = 0;

  // Populates dropdown (Set 1 hingga Set 23)
  const setSelect = document.getElementById("setSelect");
  for (let i = 1; i <= 23; i++) {
    let opt = document.createElement("option");
    opt.value = i;
    opt.textContent = `Set ${i < 10 ? '0' + i : i}`;
    setSelect.appendChild(opt);
  }

  // Muat turun soalan dari questions.json
  fetch('questions.json')
    .then(res => res.json())
    .then(data => {
      rawData = data;
      console.log("Data soalan berjaya dimuat turun:", rawData);
    })
    .catch(err => {
      console.error("Gagal membaca questions.json:", err);
      alert("Gagal memuat turun soalan. Sila pastikan fail questions.json wujud.");
    });

  function startQuiz() {
    const name = document.getElementById("studentName").value.trim();
    const className = document.getElementById("studentClass").value.trim();
    const selectedSetNum = parseInt(document.getElementById("setSelect").value);

    if (!name || !className) {
      alert("Sila isi nama dan kelas anda terlebih dahulu.");
      return;
    }

    // Cari set dalam senarai Array JSON
    const matchedSet = rawData.find(item => item.set === selectedSetNum);

    if (!matchedSet || !matchedSet.questions || matchedSet.questions.length === 0) {
      alert(`Soalan untuk Set ${selectedSetNum} tidak dijumpai atau belum sedia dalam questions.json!`);
      return;
    }

    currentQuestions = matchedSet.questions;
    userAnswers = {};

    document.getElementById("start-section").style.display = "none";
    document.getElementById("quiz-section").style.display = "block";

    document.getElementById("displayStudent").textContent = "Nama: " + name;
    document.getElementById("displayClass").textContent = "Kelas: " + className;
    document.getElementById("displaySet").textContent = "Set: " + (selectedSetNum < 10 ? '0' + selectedSetNum : selectedSetNum);

    renderQuestions();
    startTimer();
  }

  function startTimer() {
    secondsElapsed = 0;
    timerInterval = setInterval(() => {
      secondsElapsed++;
      let mins = Math.floor(secondsElapsed / 60);
      let secs = secondsElapsed % 60;
      let formattedMin = mins < 10 ? "0" + mins : mins;
      let formattedSec = secs < 10 ? "0" + secs : secs;
      document.getElementById("displayTimer").textContent = `Masa: ${formattedMin}:${formattedSec}`;
    }, 1000);
  }

  function renderQuestions() {
    const container = document.getElementById("questionsContainer");
    container.innerHTML = "";

    currentQuestions.forEach((q, index) => {
      const qCard = document.createElement("div");
      qCard.className = "question-card";

      const title = document.createElement("div");
      title.className = "question-title";
      title.textContent = `${q.no || (index + 1)}. ${q.sentence}`;
      qCard.appendChild(title);

      const grid = document.createElement("div");
      grid.className = "options-grid";

      // Render Pilihan Jawapan A, B, C
      if (q.options && Array.isArray(q.options)) {
        q.options.forEach(opt => {
          const optCard = document.createElement("div");
          optCard.className = "option-card";
          optCard.id = `q_${index}_${opt.label}`;
          optCard.onclick = () => selectOption(index, opt.label);

          const labelText = document.createElement("p");
          labelText.style.margin = "0";
          labelText.style.fontWeight = "bold";
          labelText.textContent = `(${opt.label}) ${opt.text}`;

          optCard.appendChild(labelText);
          grid.appendChild(optCard);
        });
      }

      qCard.appendChild(grid);
      container.appendChild(qCard);
    });
  }

  function selectOption(qIndex, optionLabel) {
    userAnswers[qIndex] = optionLabel;
    
    // Reset style pilihan
    const currentQuestionObj = currentQuestions[qIndex];
    if (currentQuestionObj && currentQuestionObj.options) {
      currentQuestionObj.options.forEach(opt => {
        const el = document.getElementById(`q_${qIndex}_${opt.label}`);
        if (el) el.classList.remove("selected");
      });
    }

    const selectedEl = document.getElementById(`q_${qIndex}_${optionLabel}`);
    if (selectedEl) selectedEl.classList.add("selected");
  }

  function submitQuiz() {
    if (Object.keys(userAnswers).length < currentQuestions.length) {
      if (!confirm("Anda belum menjawab semua soalan. Adakah anda pasti mahu menghantar?")) {
        return;
      }
    }

    clearInterval(timerInterval);

    // Kirim Skor mengikut pilihan 'is_correct'
    let score = 0;
    currentQuestions.forEach((q, index) => {
      const selectedLabel = userAnswers[index];
      const selectedOption = q.options.find(opt => opt.label === selectedLabel);
      if (selectedOption && selectedOption.is_correct) {
        score++;
      }
    });

    const studentName = document.getElementById("studentName").value.trim();
    const studentClass = document.getElementById("studentClass").value.trim();
    const setNum = document.getElementById("setSelect").value;
    const setName = "SET " + (setNum < 10 ? '0' + setNum : setNum);
    const scoreText = `${score} / ${currentQuestions.length}`;
    
    let mins = Math.floor(secondsElapsed / 60);
    let secs = secondsElapsed % 60;
    const timeTaken = `${mins}m ${secs}s`;

    document.getElementById("quiz-section").style.display = "none";
    document.getElementById("result-section").style.display = "block";
    document.getElementById("resultText").textContent = `Skor Anda: ${scoreText}`;
    document.getElementById("resultTime").textContent = `Masa Diambil: ${timeTaken}`;
    document.getElementById("statusMsg").textContent = "Sedang menyimpan rekod ke Google Sheet...";

    hantarRekodKeGoogleSheet(studentName, studentClass, setName, scoreText, timeTaken);
  }

  function hantarRekodKeGoogleSheet(studentName, studentClass, setName, score, timeTaken) {
    const payload = {
      studentName: studentName,
      studentClass: studentClass,
      setName: setName,
      score: score,
      timeTaken: timeTaken
    };

    fetch(GOOGLE_SCRIPT_URL, {
      method: "POST",
      mode: "no-cors",
      headers: {
        "Content-Type": "application/json"
      },
      body: JSON.stringify(payload)
    })
    .then(() => {
      document.getElementById("statusMsg").textContent = "✅ Rekod berjaya disimpan ke Google Sheet!";
      document.getElementById("statusMsg").style.color = "green";
    })
    .catch(error => {
      console.error("Gagal menghantar data:", error);
      document.getElementById("statusMsg").textContent = "❌ Ralat semasa menyimpan rekod.";
      document.getElementById("statusMsg").style.color = "red";
    });
  }
</script>

</body>
</html>
