<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Тест: Физическая безопасность (18 вопросов)</title>
  <style>
    :root {
      --bg: #f3f6fb;
      --card: #ffffff;
      --text: #1e293b;
      --muted: #64748b;
      --primary: #2563eb;
      --primary-hover: #1d4ed8;
      --border: #e2e8f0;
      --success-bg: #dcfce7;
      --success-border: #22c55e;
      --success-text: #14532d;
      --error-bg: #fee2e2;
      --error-border: #ef4444;
      --error-text: #7f1d1d;
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Inter, Arial, sans-serif;
      background-color: var(--bg);
      color: var(--text);
      line-height: 1.5;
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      align-items: center;
      padding: 20px;
    }

    .container {
      width: 100%;
      max-width: 780px;
      margin: auto;
    }

    .card {
      background: var(--card);
      border-radius: 16px;
      box-shadow: 0 10px 25px rgba(15, 23, 42, 0.06);
      border: 1px solid var(--border);
      padding: 28px;
      transition: all 0.2s ease;
    }

    /* Start Screen */
    .start-screen {
      text-align: center;
      padding: 40px 28px;
    }

    .badge {
      display: inline-block;
      background: #dbeafe;
      color: var(--primary);
      font-weight: 600;
      font-size: 13px;
      padding: 6px 14px;
      border-radius: 999px;
      margin-bottom: 16px;
    }

    h1 {
      font-size: 28px;
      font-weight: 700;
      margin-bottom: 12px;
      color: #0f172a;
    }

    .subtitle {
      color: var(--muted);
      font-size: 16px;
      max-width: 540px;
      margin: 0 auto 28px;
    }

    .settings-box {
      background: #f8fafc;
      border: 1px solid var(--border);
      border-radius: 12px;
      padding: 16px 20px;
      max-width: 440px;
      margin: 0 auto 28px;
      text-align: left;
      display: flex;
      flex-direction: column;
      gap: 12px;
    }

    .toggle-row {
      display: flex;
      align-items: center;
      justify-content: space-between;
      font-size: 15px;
      cursor: pointer;
    }

    .toggle-row input {
      width: 18px;
      height: 18px;
      accent-color: var(--primary);
      cursor: pointer;
    }

    /* Buttons */
    .btn {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 8px;
      background: var(--primary);
      color: #fff;
      font-size: 16px;
      font-weight: 600;
      padding: 13px 26px;
      border-radius: 10px;
      border: none;
      cursor: pointer;
      transition: background 0.15s ease, transform 0.1s ease;
    }

    .btn:hover:not(:disabled) {
      background: var(--primary-hover);
    }

    .btn:active:not(:disabled) {
      transform: scale(0.99);
    }

    .btn:disabled {
      opacity: 0.5;
      cursor: not-allowed;
    }

    .btn-outline {
      background: #fff;
      color: var(--text);
      border: 1px solid var(--border);
    }

    .btn-outline:hover:not(:disabled) {
      background: #f8fafc;
    }

    /* Quiz Header */
    .quiz-header {
      display: flex;
      align-items: center;
      justify-content: space-between;
      margin-bottom: 16px;
      gap: 12px;
      flex-wrap: wrap;
    }

    .progress-info {
      font-size: 15px;
      font-weight: 600;
      color: var(--muted);
    }

    .progress-info span {
      color: var(--text);
    }

    .timer-badge {
      background: #fff;
      border: 1px solid var(--border);
      padding: 6px 12px;
      border-radius: 8px;
      font-size: 14px;
      font-weight: 600;
      font-variant-numeric: tabular-nums;
      color: var(--text);
    }

    .progress-bar-wrap {
      width: 100%;
      height: 8px;
      background: #e2e8f0;
      border-radius: 999px;
      overflow: hidden;
      margin-bottom: 24px;
    }

    .progress-bar-fill {
      height: 100%;
      background: var(--primary);
      width: 0%;
      transition: width 0.3s ease;
    }

    .question-text {
      font-size: 20px;
      font-weight: 600;
      color: #0f172a;
      margin-bottom: 22px;
    }

    /* Options */
    .options-list {
      display: flex;
      flex-direction: column;
      gap: 12px;
    }

    .option-btn {
      width: 100%;
      text-align: left;
      background: #fff;
      border: 2px solid var(--border);
      border-radius: 12px;
      padding: 14px 18px;
      font-size: 16px;
      color: var(--text);
      cursor: pointer;
      display: flex;
      align-items: flex-start;
      gap: 12px;
      transition: all 0.15s ease;
      line-height: 1.45;
    }

    .option-btn:hover:not(:disabled) {
      border-color: #93c5fd;
      background: #f8fafc;
    }

    .option-index {
      flex-shrink: 0;
      width: 26px;
      height: 26px;
      border-radius: 50%;
      background: #f1f5f9;
      color: var(--muted);
      font-size: 13px;
      font-weight: 700;
      display: flex;
      align-items: center;
      justify-content: center;
      margin-top: 1px;
    }

    .option-btn.correct {
      background: var(--success-bg);
      border-color: var(--success-border);
      color: var(--success-text);
    }

    .option-btn.correct .option-index {
      background: var(--success-border);
      color: #fff;
    }

    .option-btn.wrong {
      background: var(--error-bg);
      border-color: var(--error-border);
      color: var(--error-text);
    }

    .option-btn.wrong .option-index {
      background: var(--error-border);
      color: #fff;
    }

    .option-btn:disabled {
      cursor: default;
    }

    /* Explanation */
    .explanation {
      margin-top: 20px;
      padding: 16px 18px;
      border-radius: 12px;
      background: #f8fafc;
      border-left: 4px solid var(--primary);
      font-size: 14.5px;
      color: #334155;
      display: none;
    }

    .explanation.visible {
      display: block;
      animation: fadeIn 0.2s ease;
    }

    .explanation strong {
      display: block;
      margin-bottom: 4px;
      color: #0f172a;
    }

    .quiz-footer {
      margin-top: 24px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      gap: 12px;
    }

    /* Results Screen */
    .results-header {
      text-align: center;
      padding-bottom: 24px;
      border-bottom: 1px solid var(--border);
      margin-bottom: 24px;
    }

    .score-circle {
      width: 116px;
      height: 116px;
      border-radius: 50%;
      background: #eff6ff;
      border: 4px solid var(--primary);
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      margin: 0 auto 16px;
    }

    .score-percent {
      font-size: 28px;
      font-weight: 800;
      color: var(--primary);
      line-height: 1.1;
    }

    .score-fraction {
      font-size: 13px;
      font-weight: 600;
      color: var(--muted);
    }

    .stats-grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 12px;
      margin: 20px 0;
    }

    .stat-card {
      background: #f8fafc;
      border: 1px solid var(--border);
      border-radius: 10px;
      padding: 12px;
      text-align: center;
    }

    .stat-val {
      font-size: 20px;
      font-weight: 700;
    }

    .stat-lbl {
      font-size: 12.5px;
      color: var(--muted);
    }

    .filter-bar {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 16px;
      flex-wrap: wrap;
      gap: 10px;
    }

    .filter-tabs {
      display: flex;
      gap: 8px;
    }

    .tab-btn {
      padding: 6px 14px;
      border-radius: 8px;
      border: 1px solid var(--border);
      background: #fff;
      font-size: 13.5px;
      font-weight: 600;
      cursor: pointer;
      color: var(--muted);
    }

    .tab-btn.active {
      background: var(--primary);
      color: #fff;
      border-color: var(--primary);
    }

    .review-list {
      display: flex;
      flex-direction: column;
      gap: 14px;
      max-height: 460px;
      overflow-y: auto;
      padding-right: 4px;
    }

    .review-item {
      border: 1px solid var(--border);
      border-radius: 12px;
      padding: 16px;
      background: #fff;
    }

    .review-item.is-correct {
      border-left: 4px solid var(--success-border);
    }

    .review-item.is-wrong {
      border-left: 4px solid var(--error-border);
    }

    .review-q {
      font-weight: 600;
      font-size: 15px;
      margin-bottom: 8px;
    }

    .review-ans {
      font-size: 14px;
      margin-bottom: 4px;
    }

    .hidden {
      display: none !important;
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(4px); }
      to { opacity: 1; transform: translateY(0); }
    }

    @media (max-width: 600px) {
      .card { padding: 20px; }
      h1 { font-size: 22px; }
      .question-text { font-size: 18px; }
      .stats-grid { grid-template-columns: 1fr; }
    }
  </style>
</head>
<body>

<div class="container">
  <!-- START SCREEN -->
  <div id="startScreen" class="card start-screen">
    <div class="badge">Информационная и физическая безопасность</div>
    <h1>Тренажёр по тесту «Физическая безопасность»</h1>
    <p class="subtitle">
      Все 18 вопросов собраны из экзаменационной базы. При каждом запуске порядок вопросов перемешивается случайным образом.
    </p>

    <div class="settings-box">
      <label class="toggle-row">
        <span>Перемешивать вопросы</span>
        <input type="checkbox" id="shuffleQuestionsToggle" checked disabled>
      </label>
      <label class="toggle-row">
        <span>Перемешивать варианты ответов</span>
        <input type="checkbox" id="shuffleOptionsToggle" checked>
      </label>
      <label class="toggle-row">
        <span>Показывать пояснение после ответа</span>
        <input type="checkbox" id="showExplanationToggle" checked>
      </label>
    </div>

    <button class="btn" onclick="startQuiz()">Начать тестирование</button>
  </div>

  <!-- QUIZ SCREEN -->
  <div id="quizScreen" class="hidden">
    <div class="quiz-header">
      <div class="progress-info">Вопрос <span id="currentNum">1</span> из <span id="totalNum">18</span></div>
      <div class="timer-badge" id="timerDisplay">00:00</div>
    </div>

    <div class="progress-bar-wrap">
      <div class="progress-bar-fill" id="progressBar"></div>
    </div>

    <div class="card">
      <div class="question-text" id="questionText"></div>
      <div class="options-list" id="optionsList"></div>

      <div class="explanation" id="explanationBox">
        <strong>Пояснение:</strong>
        <span id="explanationText"></span>
      </div>

      <div class="quiz-footer">
        <button class="btn btn-outline" onclick="restartQuiz()">Перемешать заново</button>
        <button class="btn" id="nextBtn" onclick="nextQuestion()" disabled>Следующий вопрос →</button>
      </div>
    </div>
  </div>

  <!-- RESULTS SCREEN -->
  <div id="resultsScreen" class="card hidden">
    <div class="results-header">
      <div class="score-circle">
        <div class="score-percent" id="scorePercent">0%</div>
        <div class="score-fraction" id="scoreFraction">0 / 18</div>
      </div>
      <h2 id="resultTitle">Тест завершён!</h2>
      <p class="subtitle" id="resultSubtitle" style="margin-bottom: 0;"></p>

      <div class="stats-grid">
        <div class="stat-card">
          <div class="stat-val" style="color: #16a34a;" id="statCorrect">0</div>
          <div class="stat-lbl">Правильных</div>
        </div>
        <div class="stat-card">
          <div class="stat-val" style="color: #dc2626;" id="statWrong">0</div>
          <div class="stat-lbl">Ошибок</div>
        </div>
        <div class="stat-card">
          <div class="stat-val" id="statTime">00:00</div>
          <div class="stat-lbl">Затрачено времени</div>
        </div>
      </div>

      <button class="btn" onclick="restartQuiz()">Пройти заново (перемешать)</button>
    </div>

    <div class="filter-bar">
      <strong>Разбор ответов</strong>
      <div class="filter-tabs">
        <button class="tab-btn active" id="tabAll" onclick="filterReview('all')">Все (18)</button>
        <button class="tab-btn" id="tabWrong" onclick="filterReview('wrong')">Только ошибки</button>
      </div>
    </div>

    <div class="review-list" id="reviewList"></div>
  </div>
</div>

<script>
  const QUESTIONS_DB = [
    {
      id: 1,
      question: "Как хладон борется с пожаром?",
      options: [
        { text: "Он нарушает химическую реакцию горения", isCorrect: true },
        { text: "Он сокращает способность поглощения топлива огнем", isCorrect: false },
        { text: "Он уменьшает содержание кислорода в горящей области", isCorrect: false },
        { text: "Он понижает температуру горящей области, уменьшая интенсивность огня", isCorrect: false }
      ],
      explanation: "Газовые огнетушащие составы на основе хладона (галоны) ингибируют (разрывают) цепную химическую реакцию горения на молекулярном уровне."
    },
    {
      id: 2,
      question: "Если шифро-замок (cipher lock) имеет функцию дверного таймера, что это означает?",
      options: [
        { text: "Если дверь была открыта больше определенного времени, включается сигнал тревоги", isCorrect: true },
        { text: "Он может быть открыт только в аварийных ситуациях", isCorrect: false },
        { text: "Он имеет возможность включения сигнала тревоги при открытии под принуждением", isCorrect: false },
        { text: "Он имеет возможность замещения ключа контролирующим персоналом", isCorrect: false }
      ],
      explanation: "Функция дверного таймера (door timer / door delay) отслеживает длительность открытия двери и подаёт сигнал тревоги, если дверь остаётся открытой или подпёртой дольше заданного интервала."
    },
    {
      id: 3,
      question: "Какой из приведенных ниже ответов содержит категорию защитных мер, не относящихся к программе физической безопасности?",
      options: [
        { text: "Реакция и выявление", isCorrect: false },
        { text: "Задерживание и освещение", isCorrect: false },
        { text: "Оценка и выявление", isCorrect: false },
        { text: "Сдерживание и задерживание", isCorrect: true }
      ],
      explanation: "В классической модели физической безопасности выделяют сдерживание, задерживание, выявление, оценку и реагирование. В данном вопросе экзаменационной базы корректным ключом является вариант «Сдерживание и задерживание»."
    },
    {
      id: 4,
      question: "Что означает «положительное давление» по отношению к вентиляции?",
      options: [
        { text: "Когда дверь открывается, воздух выходит из помещения", isCorrect: true },
        { text: "Когда дверь открывается, воздух поступает внутрь помещения", isCorrect: false },
        { text: "При пожаре дым отводится в одно помещение", isCorrect: false },
        { text: "При пожаре источники электропитания отключаются", isCorrect: false }
      ],
      explanation: "При положительном давлении (подпоре воздуха) давление внутри защищаемого помещения выше, чем снаружи, поэтому при открытии двери воздух выходит наружу, препятствуя попаданию пыли и дыма внутрь."
    },
    {
      id: 5,
      question: "Что такое шифро-замок (cipher lock)?",
      options: [
        { text: "Замок, который использует криптографические ключи", isCorrect: false },
        { text: "Замок, который использует такой тип ключей, которые не могут быть скопированы", isCorrect: false },
        { text: "Замок, который использует клавиатуру", isCorrect: true },
        { text: "Замок, который использует токены и считыватели по периметру", isCorrect: false }
      ],
      explanation: "Шифро-замок (cipher lock) — это механический или электронный кодовый замок с кнопочной клавиатурой для набора секретной комбинации."
    },
    {
      id: 6,
      question: "Что не является препятствием для установки систем выявления вторжений и мониторинга?",
      options: [
        { text: "Они требуют реакции людей", isCorrect: false },
        { text: "Их нельзя обойти", isCorrect: true },
        { text: "Их установка стоит дорого", isCorrect: false },
        { text: "Они являются источником ложных срабатываний", isCorrect: false }
      ],
      explanation: "Любую систему выявления вторжений потенциально можно обойти, а главными сложностями при внедрении являются высокая стоимость, ложные срабатывания и необходимость реагирования персонала."
    },
    {
      id: 7,
      question: "Какой из перечисленных ниже ответов лучше всего описывает отношения между анализом рисков, приемлемым уровнем рисков, базисами, контрмерами и метриками?",
      options: [
        { text: "Результаты анализа рисков помогают руководству понять и установить приемлемый уровень рисков. Базисы основаны на этом уровне. Метрики используются для отслеживания эффективности контрмер, чтобы убедиться в соблюдении базисов.", isCorrect: true },
        { text: "Результаты анализа рисков используются для определения необходимых контрмер. Базисы используются для оценки этих контрмер. Метрики используются для отслеживания эффективности контрмер, чтобы убедиться в соблюдении базисов.", isCorrect: false },
        { text: "Результаты анализа рисков помогают руководству понять и установить приемлемый уровень рисков. Базисы основаны на этом уровне. Метрики используются для отслеживания эффективности базисов.", isCorrect: false },
        { text: "Результаты анализа рисков помогают руководству понять и установить базисы. Приемлемый уровень рисков основан на базисах. Метрики используются для отслеживания эффективности контрмер, чтобы убедиться в соблюдении базисов.", isCorrect: false }
      ],
      explanation: "Сначала анализ рисков определяет приемлемый уровень риска; на его основе формируются минимальные требования безопасности (базисы), реализуемые через контрмеры, а метрики измеряют эффективность этих контрмер."
    },
    {
      id: 8,
      question: "Что из приведенного ниже не является правильным утверждением в отношении электростатической системы выявления вторжений?",
      options: [
        { text: "Она создает электростатическое поле и контролирует изменение его емкости", isCorrect: false },
        { text: "Она может выявить проникновение нарушителя в определенные границы вокруг объекта", isCorrect: false },
        { text: "Она может использоваться в качестве системы выявления вторжений для больших областей (помещений)", isCorrect: true },
        { text: "Она контролирует баланс между электрической емкостью и индуктивностью объекта D. Она может выявить проникновение нарушителя в определенные границы вокруг объекта", isCorrect: false }
      ],
      explanation: "Электростатические (ёмкостные) датчики работают в непосредственной близости от охраняемого провода, ограждения или конкретного предмета, а не для покрытия больших открытых пространств или целых помещений."
    },
    {
      id: 9,
      question: "Что такое шлюз (mantrap)?",
      options: [
        { text: "Комната с двумя дверями, используемая для физического контроля доступа", isCorrect: true },
        { text: "Доверенный домен безопасности", isCorrect: false },
        { text: "Устройство пожаротушения", isCorrect: false },
        { text: "Механизм логического управления доступом", isCorrect: false }
      ],
      explanation: "Шлюзовая кабина (mantrap) — это небольшое помещение с двумя взаимосвязанными дверями: вторая дверь не откроется, пока первая не будет полностью закрыта и не пройдёт проверка."
    },
    {
      id: 10,
      question: "Что из перечисленного ниже не является основным компонентом CPTED?",
      options: [
        { text: "Естественное наблюдение", isCorrect: false },
        { text: "Укрепление территории", isCorrect: false },
        { text: "Нацеленность на укрепленность", isCorrect: true },
        { text: "Естественное управление доступом", isCorrect: false }
      ],
      explanation: "Тремя базовыми принципами проектирования безопасной среды (CPTED) являются естественное наблюдение (natural surveillance), естественное управление доступом (natural access control) и территориальное укрепление (territorial reinforcement)."
    },
    {
      id: 11,
      question: "Что из перечисленного ниже не является задерживающим механизмом?",
      options: [
        { text: "Замки", isCorrect: false },
        { text: "Контроль доступа", isCorrect: false },
        { text: "Внутренние защитные средства", isCorrect: false },
        { text: "Предупреждающие знаки", isCorrect: true }
      ],
      explanation: "Предупреждающие знаки относятся к мерам сдерживания (deterrence) — они отпугивают нарушителя психологически, но физически не задерживают его продвижение, в отличие от замков и барьеров."
    },
    {
      id: 12,
      question: "Если механизм контроля доступа является «нормально открытым» (fail-safe), а не «нормально закрытым» (fail-secure), что это означает?",
      options: [
        { text: "По умолчанию открыт", isCorrect: true },
        { text: "По умолчанию закрыт", isCorrect: false },
        { text: "По умолчанию передает сигнал тревоги, а не включает его в месте своего нахождения", isCorrect: false },
        { text: "По умолчанию «нет доступа»", isCorrect: false }
      ],
      explanation: "Режим fail-safe («безопасный при отказе» для жизни людей) означает, что при отключении питания замок автоматически разблокируется и остаётся открытым для свободной эвакуации."
    },
    {
      id: 13,
      question: "Что является первым шагом, который нужно предпринять при выявлении пожара?",
      options: [
        { text: "Отключить систему HVAC и активировать открытие пожарных выходов", isCorrect: false },
        { text: "Посоветовать людям покинуть здание", isCorrect: true },
        { text: "Активировать систему пожаротушения", isCorrect: false },
        { text: "Определить тип пожара", isCorrect: false }
      ],
      explanation: "Главный приоритет при любом пожаре — спасение человеческих жизней, поэтому первым делом необходимо оповестить людей и организовать эвакуацию из здания."
    },
    {
      id: 14,
      question: "Что не является административными мерами, относящимися к процедурам действий в аварийных ситуациях?",
      options: [
        { text: "Обучение и повышение осведомленности", isCorrect: false },
        { text: "Делегирование обязанностей", isCorrect: false },
        { text: "Системы выявления вторжений", isCorrect: true },
        { text: "Тренировки и проверки", isCorrect: false }
      ],
      explanation: "Системы выявления вторжений (IDS) являются техническими (физическими) средствами контроля, тогда как обучение, распределение ролей и учения — это административные меры."
    },
    {
      id: 15,
      question: "Когда охранники являются лучшим выбором в качестве механизма физического контроля доступа?",
      options: [
        { text: "Когда бюджет безопасности мал", isCorrect: false },
        { text: "Когда необходимо принимать обдуманные решения в различных ситуациях", isCorrect: true },
        { text: "Когда внедрены меры контроля доступа", isCorrect: false },
        { text: "Когда требуется выявлять вторжения", isCorrect: false }
      ],
      explanation: "Люди (охранники) незаменимы там, где требуются гибкость, оценка контекста и принятие нестандартных решений, недоступных автоматизированным турникетам и замкам."
    },
    {
      id: 16,
      question: "Какие проблемы могут быть вызваны влажностью в помещениях с электрическим оборудованием?",
      options: [
        { text: "Высокая влажность может вызвать коррозию, а низкая - привести к статическому электричеству", isCorrect: true },
        { text: "Высокая влажность может вызвать коррозию, а низкая - привести к перепадам напряжения", isCorrect: false },
        { text: "Высокая влажность может вызвать перепады напряжения, а низкая - привести к статическому электричеству", isCorrect: false },
        { text: "Высокая влажность может привести к повышению напряжения, а низкая влажность - вызвать коррозию", isCorrect: false }
      ],
      explanation: "Избыточная влажность приводит к конденсации влаги и коррозии контактов, а слишком сухой воздух способствует накоплению опасных электростатических зарядов (ESD)."
    },
    {
      id: 17,
      question: "Когда следует использовать огнетушитель Класса С вместо огнетушителя Класса А?",
      options: [
        { text: "Когда пожар происходит в открытом пространстве", isCorrect: false },
        { text: "Когда горят горючие жидкости", isCorrect: false },
        { text: "Когда горит электрическое оборудование", isCorrect: true },
        { text: "Когда горит дерево или бумага", isCorrect: false }
      ],
      explanation: "По международной классификации (NFPA), используемой в данном тесте: Класс A — обычные твёрдые материалы (дерево, бумага), Класс B — жидкости, Класс C — электрооборудование под напряжением."
    },
    {
      id: 18,
      question: "Что является наиболее частой проблемой с датчиками, выявляющими вибрацию, при их использовании для безопасности периметра?",
      options: [
        { text: "Они вызывают ложные срабатывания", isCorrect: true },
        { text: "Они создают помехи для компьютерного оборудования", isCorrect: false },
        { text: "Источники энергии для них могут быть легко отключены", isCorrect: false },
        { text: "Они могут быть обезврежены путем направления определенных электрических сигналов в защищаемую область", isCorrect: false }
      ],
      explanation: "Вибрационные датчики на ограждениях чувствительны к ветру, граду, проезжающему транспорту и животным, что часто приводит к ложным срабатываниям."
    }
  ];

  let activeQuestions = [];
  let currentIndex = 0;
  let score = 0;
  let userAnswers = [];
  let timerInterval = null;
  let secondsElapsed = 0;

  // Перемешивание Фишера-Йейтса
  function shuffleArray(array) {
    const arr = [...array];
    for (let i = arr.length - 1; i > 0; i--) {
      const j = Math.floor(Math.random() * (i + 1));
      [arr[i], arr[j]] = [arr[j], arr[i]];
    }
    return arr;
  }

  function formatTime(sec) {
    const mins = String(Math.floor(sec / 60)).padStart(2, '0');
    const secs = String(sec % 60).padStart(2, '0');
    return `${mins}:${secs}`;
  }

  function startTimer() {
    clearInterval(timerInterval);
    secondsElapsed = 0;
    document.getElementById('timerDisplay').textContent = '00:00';
    timerInterval = setInterval(() => {
      secondsElapsed++;
      document.getElementById('timerDisplay').textContent = formatTime(secondsElapsed);
    }, 1000);
  }

  function startQuiz() {
    const shuffleOptions = document.getElementById('shuffleOptionsToggle').checked;

    activeQuestions = shuffleArray(QUESTIONS_DB).map(q => ({
      ...q,
      options: shuffleOptions ? shuffleArray(q.options) : [...q.options]
    }));

    currentIndex = 0;
    score = 0;
    userAnswers = [];

    document.getElementById('totalNum').textContent = activeQuestions.length;
    document.getElementById('startScreen').classList.add('hidden');
    document.getElementById('resultsScreen').classList.add('hidden');
    document.getElementById('quizScreen').classList.remove('hidden');

    startTimer();
    renderQuestion();
  }

  function restartQuiz() {
    startQuiz();
  }

  function renderQuestion() {
    const q = activeQuestions[currentIndex];
    const total = activeQuestions.length;

    document.getElementById('currentNum').textContent = currentIndex + 1;
    document.getElementById('progressBar').style.width = `${(currentIndex / total) * 100}%`;
    document.getElementById('questionText').textContent = q.question;

    const optionsList = document.getElementById('optionsList');
    optionsList.innerHTML = '';

    q.options.forEach((opt, idx) => {
      const btn = document.createElement('button');
      btn.className = 'option-btn';
      btn.innerHTML = `
        <span class="option-index">${idx + 1}</span>
        <span>${opt.text}</span>
      `;
      btn.onclick = () => selectOption(idx);
      optionsList.appendChild(btn);
    });

    const expBox = document.getElementById('explanationBox');
    expBox.classList.remove('visible');

    const nextBtn = document.getElementById('nextBtn');
    nextBtn.disabled = true;
    nextBtn.textContent = currentIndex === total - 1 ? 'Завершить тест' : 'Следующий вопрос →';
  }

  function selectOption(selectedIdx) {
    const q = activeQuestions[currentIndex];
    const buttons = document.querySelectorAll('.option-btn');
    const selectedOpt = q.options[selectedIdx];
    const correctOpt = q.options.find(o => o.isCorrect);

    if (selectedOpt.isCorrect) {
      score++;
    }

    userAnswers.push({
      question: q.question,
      selectedText: selectedOpt.text,
      correctText: correctOpt.text,
      isCorrect: selectedOpt.isCorrect,
      explanation: q.explanation
    });

    buttons.forEach((btn, idx) => {
      btn.disabled = true;
      if (q.options[idx].isCorrect) {
        btn.classList.add('correct');
      } else if (idx === selectedIdx && !selectedOpt.isCorrect) {
        btn.classList.add('wrong');
      }
    });

    if (document.getElementById('showExplanationToggle').checked) {
      document.getElementById('explanationText').textContent = q.explanation;
      document.getElementById('explanationBox').classList.add('visible');
    }

    document.getElementById('nextBtn').disabled = false;
  }

  function nextQuestion() {
    currentIndex++;
    if (currentIndex < activeQuestions.length) {
      renderQuestion();
    } else {
      showResults();
    }
  }

  function showResults() {
    clearInterval(timerInterval);
    document.getElementById('quizScreen').classList.add('hidden');
    document.getElementById('resultsScreen').classList.remove('hidden');

    const total = activeQuestions.length;
    const percent = Math.round((score / total) * 100);
    const wrongCount = total - score;

    document.getElementById('scorePercent').textContent = `${percent}%`;
    document.getElementById('scoreFraction').textContent = `${score} / ${total}`;
    document.getElementById('statCorrect').textContent = score;
    document.getElementById('statWrong').textContent = wrongCount;
    document.getElementById('statTime').textContent = formatTime(secondsElapsed);

    document.getElementById('tabAll').textContent = `Все (${total})`;
    document.getElementById('tabWrong').textContent = `Только ошибки (${wrongCount})`;

    let title = 'Отличный результат!';
    let subtitle = 'Вы уверенно владеете материалом по физической безопасности.';
    if (percent < 50) {
      title = 'Стоит повторить материал';
      subtitle = 'Изучите пояснения к ошибкам ниже и попробуйте снова.';
    } else if (percent < 80) {
      title = 'Хороший результат!';
      subtitle = 'Есть пара неточностей, разберите ошибки для закрепления.';
    }

    document.getElementById('resultTitle').textContent = title;
    document.getElementById('resultSubtitle').textContent = subtitle;

    filterReview('all');
  }

  function filterReview(mode) {
    document.getElementById('tabAll').classList.toggle('active', mode === 'all');
    document.getElementById('tabWrong').classList.toggle('active', mode === 'wrong');

    const list = document.getElementById('reviewList');
    list.innerHTML = '';

    const filtered = mode === 'wrong'
      ? userAnswers.filter(a => !a.isCorrect)
      : userAnswers;

    if (filtered.length === 0) {
      list.innerHTML = '<div style="text-align:center; color:#64748b; padding:24px;">Ошибок нет — все ответы верные!</div>';
      return;
    }

    filtered.forEach((item, index) => {
      const div = document.createElement('div');
      div.className = `review-item ${item.isCorrect ? 'is-correct' : 'is-wrong'}`;
      div.innerHTML = `
        <div class="review-q">${index + 1}. ${item.question}</div>
        <div class="review-ans" style="color: ${item.isCorrect ? '#15803d' : '#b91c1c'};">
          <strong>Ваш ответ:</strong> ${item.selectedText}
        </div>
        ${!item.isCorrect ? `
          <div class="review-ans" style="color: #15803d;">
            <strong>Правильный ответ:</strong> ${item.correctText}
          </div>
        ` : ''}
        <div style="font-size: 13.5px; color: #475569; margin-top: 6px;">
          ${item.explanation}
        </div>
      `;
      list.appendChild(div);
    });
  }
</script>

</body>
</html>
