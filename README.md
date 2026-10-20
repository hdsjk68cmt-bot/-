
<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Youth On</title>

<style>
* {
  box-sizing: border-box;
}

body {
  margin: 0;
  font-family: Arial, "Noto Sans KR", sans-serif;
  background: #eef7ff;
  color: #173653;
}

button, input {
  font: inherit;
}

button {
  cursor: pointer;
}

.app {
  width: 100%;
  max-width: 500px;
  min-height: 100vh;
  margin: auto;
  padding: 20px;
  background: linear-gradient(#ffffff, #edf8ff);
}

header {
  display: flex;
  align-items: center;
  gap: 12px;
  margin-bottom: 24px;
}

.logo {
  width: 190px;
  height: 85px;
  object-fit: contain;
  object-position: left;
}

.back {
  padding: 10px 14px;
  border: none;
  border-radius: 12px;
  background: #dff1ff;
  color: #076ac0;
}

.page {
  display: none;
}

.page.active {
  display: block;
}

h1 {
  font-size: 27px;
  margin-bottom: 10px;
}

p {
  color: #71869b;
  line-height: 1.7;
}

.primary {
  width: 100%;
  padding: 16px;
  border: none;
  border-radius: 15px;
  background: linear-gradient(100deg, #0756b5, #16b5e5);
  color: white;
  font-weight: bold;
  margin-top: 12px;
}

.cards {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  gap: 12px;
  margin-top: 22px;
}

.card {
  padding: 17px 12px;
  text-align: left;
  background: white;
  border: 1px solid #d8ebfa;
  border-radius: 18px;
  box-shadow: 0 5px 15px #b7d8ef22;
  color: #173653;
}

.card .emoji {
  display: block;
  font-size: 32px;
  margin-bottom: 12px;
}

.card strong {
  display: block;
  margin-bottom: 8px;
}

.card small {
  color: #71869b;
  line-height: 1.5;
}

.wide {
  grid-column: 1 / -1;
}

.welcome {
  margin-top: 25px;
  padding: 35px 10px;
  border-radius: 25px;
  background: linear-gradient(135deg, #d9f1ff, #f4fbff);
  text-align: center;
}

.friends {
  font-size: 70px;
}

.item {
  width: 100%;
  display: flex;
  gap: 12px;
  align-items: flex-start;
  padding: 15px;
  margin: 12px 0;
  border: 1px solid #d8ebfa;
  border-radius: 17px;
  background: white;
  text-align: left;
  color: #173653;
}

.item-emoji {
  font-size: 30px;
}

.item-info {
  flex: 1;
  line-height: 1.6;
}

.item-info small {
  display: block;
  color: #71869b;
  margin-top: 4px;
}

.tag {
  display: inline-block;
  padding: 4px 8px;
  margin: 5px 4px 0 0;
  border-radius: 15px;
  background: #e5f4ff;
  color: #075bb0;
  font-size: 12px;
}

.field {
  width: 100%;
  padding: 13px;
  margin: 8px 0 15px;
  border: 1px solid #cfe3f4;
  border-radius: 12px;
  background: white;
}

.label {
  font-weight: bold;
  font-size: 14px;
}

.notice {
  margin-top: 16px;
  padding: 13px;
  border-radius: 12px;
  background: #e6f5ff;
  color: #51758f;
  font-size: 12px;
  line-height: 1.7;
}

/* 채팅 화면 */
.chat {
  overflow: hidden;
  border: 1px solid #dbe8f0;
  border-radius: 20px;
  background: white;
}

.chat-header {
  padding: 15px;
  border-bottom: 1px solid #eee;
  font-weight: bold;
}

.messages {
  height: 360px;
  overflow-y: auto;
  padding: 14px;
  background: #dceaf1;
}

.message {
  margin: 13px 0;
}

.message .name {
  margin-bottom: 5px;
  font-size: 12px;
  color: #607a8c;
}

.bubble {
  display: inline-block;
  max-width: 85%;
  padding: 11px 13px;
  border-radius: 4px 15px 15px;
  background: white;
  overflow-wrap: anywhere;
}

.message.mine {
  text-align: right;
}

.message.mine .bubble {
  background: #ffeb65;
  border-radius: 15px 4px 15px 15px;
  text-align: left;
}

.chat-form {
  display: flex;
  gap: 7px;
  padding: 10px;
}

.chat-form input {
  width: 100%;
  min-width: 0;
  padding: 12px;
  border: 1px solid #ddd;
  border-radius: 22px;
}

.chat-form button {
  border: none;
  border-radius: 13px;
  padding: 0 16px;
  background: #ffeb65;
}

.secondary {
  width: 100%;
  padding: 14px;
  margin-top: 10px;
  border: none;
  border-radius: 13px;
  background: #dff2ff;
  color: #075bb0;
  font-weight: bold;
}

.video {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 200px;
  margin: 20px 0;
  border-radius: 20px;
  color: white;
  background: linear-gradient(135deg, #0756b5, #19b5e3);
  font-size: 45px;
}

.video small {
  margin-top: 10px;
  font-size: 13px;
}

.empty {
  padding: 25px;
  text-align: center;
  color: #71869b;
}

</style>
</head>

<body>
<div class="app">

<header>
  <button class="back" id="back" onclick="goBack()" hidden>
    ←
  </button>

  <!-- 로고 이미지 파일을 youth-on-logo.png로 올려 주세요 -->
  <img
    class="logo"
    src="youth-on-logo.png"
    alt="Youth On 로고"
    onerror="this.style.display='none';document.getElementById('logoText').hidden=false"
  >

  <strong id="logoText" hidden style="color:#087bd2;font-size:25px">
    YOUTH ON
  </strong>
</header>

<!-- 첫 화면 -->
<section class="page active" id="home">
  <h1 style="text-align:center">우리의 즐거움, ON!</h1>
  <p style="text-align:center">
    운동하고, 요리하고, 새로운 친구를 만나봐요.
  </p>

  <button class="primary" onclick="go('choose')">
    참가하기 →
  </button>

  <div class="welcome">
    <div class="friends">🧑🏻‍🤝‍🧑🏻</div>
    <h2>청소년 여러분, 환영해요!</h2>
    <p>함께라서 더 즐거운 Youth On</p>
  </div>
</section>

<!-- 온라인 / 오프라인 선택 -->
<section class="page" id="choose">
  <h1>어떤 활동을 할까요?</h1>
  <p>원하는 활동 방식을 선택해 주세요.</p>

  <div class="cards">
    <button class="card" onclick="go('offline')">
      <span class="emoji">🏃</span>
      <strong>오프라인</strong>
      <small>직접 만나 함께 즐겨요.</small>
    </button>

    <button class="card" onclick="go('online')">
      <span class="emoji">💻</span>
      <strong>온라인</strong>
      <small>채팅과 영상으로 만나요.</small>
    </button>
  </div>
</section>

<!-- 오프라인 -->
<section class="page" id="offline">
  <h1>오프라인 활동</h1>
  <p>친구들과 직접 만나 즐겨보세요.</p>

  <div class="cards">
    <button class="card" onclick="showActivities('sports')">
      <span class="emoji">⚽</span>
      <strong>스포츠</strong>
      <small>축구, 농구, 배드민턴</small>
    </button>

    <button class="card" onclick="showActivities('food')">
      <span class="emoji">🍜</span>
      <strong>먹거리</strong>
      <small>맛집과 디저트 탐방</small>
    </button>

    <button class="card wide" onclick="showActivities('play')">
      <span class="emoji">🎳</span>
      <strong>놀이</strong>
      <small>보드게임, 볼링 등</small>
    </button>
  </div>
</section>

<!-- 오프라인 세부 활동 -->
<section class="page" id="activities">
  <h1 id="activityTitle">활동 목록</h1>
  <p>인원과 장소를 확인하고 선택하세요.</p>
  <div id="activityList"></div>
</section>

<!-- 신청 -->
<section class="page" id="apply">
  <h1>모임 참가 신청</h1>
  <div id="applyInfo" class="notice"></div>

  <label class="label" for="nickname">참가자 별명</label>
  <input class="field" id="nickname" maxlength="20"
    placeholder="사용할 별명을 입력하세요">

  <label class="label" for="date">희망 날짜</label>
  <input class="field" id="date" type="date">

  <label class="label" for="message">하고 싶은 말</label>
  <input class="field" id="message" maxlength="100"
    placeholder="선택 사항">

  <button class="primary" onclick="applyActivity()">
    신청 내용 저장하기
  </button>
  <div id="applyResult" class="notice" hidden></div>
</section>

<!-- 온라인 -->
<section class="page" id="online">
  <h1>온라인 활동</h1>
  <p>집에서도 관심사가 같은 친구들과 함께해요.</p>

  <div class="cards">
    <button class="card" onclick="go('rooms')">
      <span class="emoji">💬</span>
      <strong>소모임 채팅방</strong>
      <small>친구들과 관심사를 나눠요.</small>
    </button>

    <button class="card" onclick="go('cooking')">
      <span class="emoji">👩‍🍳</span>
      <strong>쿠킹 클래스</strong>
      <small>요리 수업과 영상</small>
    </button>
  </div>
</section>

<!-- 채팅방 목록 -->
<section class="page" id="rooms">
  <h1>소모임 채팅방</h1>
  <p>관심 있는 채팅방을 선택해 보세요.</p>

  <input class="field" id="roomSearch"
    placeholder="채팅방 검색" oninput="renderRooms()">

  <div id="roomList"></div>

  <div class="notice">
    표시되는 참여 인원은 예시입니다.
    여러 사용자가 실시간으로 대화하려면 서버 연결이 필요합니다.
  </div>
</section>

<!-- 채팅 -->
<section class="page" id="chat">
  <div class="chat">
    <div class="chat-header" id="chatTitle">
      💬 채팅방
    </div>

    <div class="messages" id="messages"></div>

    <form class="chat-form" onsubmit="sendMessage(event)">
      <input id="chatInput" maxlength="250"
        placeholder="메시지를 입력하세요" autocomplete="off">
      <button type="submit">➤</button>
    </form>
  </div>

  <div class="notice">
    이 버전의 메시지는 현재 브라우저에만 저장됩니다.
    실제 다른 사용자에게 전송되지는 않습니다.
  </div>
</section>

<!-- 쿠킹 카테고리 -->
<section class="page" id="cooking">
  <h1>쿠킹 클래스</h1>
  <p>배우고 싶은 요리 분야를 선택하세요.</p>

  <div class="cards">
    <button class="card" onclick="showClasses('베이킹')">
      <span class="emoji">🥐</span>
      <strong>베이킹</strong>
      <small>쿠키, 케이크, 빵</small>
    </button>

    <button class="card" onclick="showClasses('양식')">
      <span class="emoji">🍝</span>
      <strong>양식</strong>
      <small>파스타와 샐러드</small>
    </button>

    <button class="card" onclick="showClasses('한식')">
      <span class="emoji">🍚</span>
      <strong>한식</strong>
      <small>친숙한 집밥 요리</small>
    </button>

    <button class="card" onclick="showClasses('일식')">
      <span class="emoji">🍙</span>
      <strong>일식</strong>
      <small>간단한 일본 요리</small>
    </button>
  </div>
</section>

<!-- 쿠킹 클래스 목록 -->
<section class="page" id="classes">
  <h1 id="classTitle">클래스 목록</h1>
  <p>수업과 인원, 가격을 확인하세요.</p>
  <div id="classList"></div>
</section>

<!-- 수업 상세 -->
<section class="page" id="lesson">
  <div class="video">▶<small>쿠킹 영상 클래스</small></div>

  <h1 id="lessonTitle">쿠킹 클래스</h1>
  <p id="lessonInfo"></p>

  <label class="label" for="videoUrl">영상 주소</label>
  <input class="field" id="videoUrl"
    placeholder="영상 URL 입력 (선택 사항)">

  <button class="secondary" onclick="openVideo()">
    영상 열기
  </button>

  <button class="primary" onclick="joinClass()">
    클래스 가입하기
  </button>
</section>

<section class="page" id="myClasses">
  <h1>내 쿠킹 클래스</h1>
  <div id="myClassList"></div>
</section>

</div>

<script>
const $ = id => document.getElementById(id);

let historyPages = ["home"];
let currentActivity = null;
let currentClass = null;
let currentRoom = null;

function go(id) {
  document.querySelectorAll(".page").forEach(page => {
    page.classList.toggle("active", page.id === id);
  });

  if (historyPages[historyPages.length - 1] !== id) {
    historyPages.push(id);
  }

  $("back").hidden = id === "home";
  window.scrollTo(0, 0);
}

function goBack() {
  if (historyPages.length <= 1) return;
  historyPages.pop();

  const previous = historyPages[historyPages.length - 1];

  document.querySelectorAll(".page").forEach(page => {
    page.classList.toggle("active", page.id === previous);
  });

  $("back").hidden = previous === "home";
  window.scrollTo(0, 0);
}

function readData(key) {
  try {
    const value = JSON.parse(localStorage.getItem(key));
    return Array.isArray(value) ? value : [];
  } catch (error) {
    return [];
  }
}

function saveData(key, value) {
  try {
    localStorage.setItem(key, JSON.stringify(value));
    return true;
  } catch (error) {
    alert("저장할 수 없어요. 브라우저 설정을 확인해 주세요.");
    return false;
  }
}

const activities = {
  sports: {
    title: "스포츠 모임",
    items: [
      {
        emoji: "⚽",
        name: "청소년 축구 모임",
        people: 8,
        place: "지역 공공 운동장",
        detail: "초보자도 함께 즐기는 친목 축구"
      },
      {
        emoji: "🏀",
        name: "농구 친구들",
        people: 6,
        place: "지역 체육관",
        detail: "농구를 연습하고 친선 경기를 해요."
      },
      {
        emoji: "🏸",
        name: "배드민턴 모임",
        people: 5,
        place: "지역 실내 체육관",
        detail: "친구들과 배드민턴을 즐겨요."
      }
    ]
  },

  food: {
    title: "먹거리 모임",
    items: [
      {
        emoji: "🍜",
        name: "맛집 탐방",
        people: 5,
        place: "지역 중심가",
        detail: "새로운 메뉴를 함께 찾아봐요."
      },
      {
        emoji: "🥐",
        name: "빵지순례",
        people: 4,
        place: "지역 베이커리",
        detail: "다양한 빵과 디저트를 구경해요."
      }
    ]
  },

  play: {
    title: "놀이 모임",
    items: [
      {
        emoji: "🎲",
        name: "보드게임 친구들",
        people: 6,
        place: "청소년 문화 공간",
        detail: "보드게임을 함께 즐겨요."
      },
      {
        emoji: "🎳",
        name: "볼링 모임",
        people: 4,
        place: "지역 볼링장",
        detail: "처음 하는 친구도 함께해요."
      }
    ]
  }
};

function addItem(container, emoji, title, detail, tags, callback) {
  const button = document.createElement("button");
  button.className = "item";

  const icon = document.createElement("span");
  icon.className = "item-emoji";
  icon.textContent = emoji;

  const info = document.createElement("div");
  info.className = "item-info";

  const strong = document.createElement("strong");
  strong.textContent = title;
  info.appendChild(strong);

  const tagLine = document.createElement("div");

  tags.forEach(text => {
    const tag = document.createElement("span");
    tag.className = "tag";
    tag.textContent = text;
    tagLine.appendChild(tag);
  });

  info.appendChild(tagLine);

  const small = document.createElement("small");
  small.textContent = detail;
  info.appendChild(small);

  button.append(icon, info);
  button.addEventListener("click", callback);
  container.appendChild(button);
}

function showActivities(category) {
  const data = activities[category];

  $("activityTitle").textContent = data.title;

  const list = $("activityList");
  list.replaceChildren();

  data.items.forEach(item => {
    addItem(
      list,
      item.emoji,
      item.name,
      item.detail,
      ["👥 " + item.people + "명", "📍 " + item.place],
      () => selectActivity(item)
    );
  });

  go("activities");
}

function selectActivity(item) {
  currentActivity = item;

  $("applyInfo").textContent =
    item.emoji + " " + item.name +
    " · " + item.place +
    " · 현재 참여 인원 " + item.people + "명";

  $("nickname").value = "";
  $("date").value = "";
  $("message").value = "";
  $("applyResult").hidden = true;

  go("apply");
}

function applyActivity() {
  if (!currentActivity) return;

  const nickname = $("nickname").value.trim();

  if (!nickname) {
    alert("참가자 별명을 입력해 주세요.");
    $("nickname").focus();
    return;
  }

  const applications = readData("youthOnApplications");

  applications.unshift({
    name: currentActivity.name,
    emoji: currentActivity.emoji,
    place: currentActivity.place,
    nickname: nickname,
    date: $("date").value,
    message: $("message").value.trim()
  });

  if (saveData("youthOnApplications", applications)) {
    $("applyResult").textContent =
      "신청 내용이 이 기기에 저장되었어요!";
    $("applyResult").hidden = false;
  }
}

const rooms = [
  {
    id: "sports",
    emoji: "⚽",
    name: "스포츠 수다방",
    people: 18,
    detail: "축구, 농구, 운동 이야기"
  },
  {
    id: "cooking",
    emoji: "🍳",
    name: "요리 초보 모임",
    people: 12,
    detail: "레시피와 요리 질문"
  },
  {
    id: "hobby",
    emoji: "🎨",
    name: "취미 친구 찾기",
    people: 24,
    detail: "그림, 음악, 취미 이야기"
  },
  {
    id: "study",
    emoji: "📚",
    name: "공부 친구방",
    people: 15,
    detail: "공부 팁과 응원"
  }
];

function renderRooms() {
  const list = $("roomList");
  list.replaceChildren();

  const query = $("roomSearch").value.trim().toLowerCase();

  const filtered = rooms.filter(room =>
    (room.name + " " + room.detail).toLowerCase().includes(query)
  );

  if (filtered.length === 0) {
    list.innerHTML = '<div class="empty">검색 결과가 없어요.</div>';
    return;
  }

  filtered.forEach(room => {
    addItem(
      list,
      room.emoji,
      room.name,
      room.detail,
      ["👥 " + room.people + "명 참여"],
      () => openRoom(room)
    );
  });
}

function openRoom(room) {
  currentRoom = room;

  $("chatTitle").textContent =
    room.emoji + " " + room.name +
    " · " + room.people + "명";

  renderMessages();
  go("chat");
}

function renderMessages() {
  const list = $("messages");
  list.replaceChildren();

  const messages = readData("youthOnChat_" + currentRoom.id);

  if (messages.length === 0) {
    const welcome = document.createElement("div");
    welcome.className = "message";

    const name = document.createElement("div");
    name.className = "name";
    name.textContent = currentRoom.name;

    const bubble = document.createElement("div");
    bubble.className = "bubble";
    bubble.textContent = "안녕하세요! 서로 존중하며 이야기해요 😊";

    welcome.append(name, bubble);
    list.appendChild(welcome);
  }

  messages.forEach(message => {
    const row = document.createElement("div");
    row.className = message.mine ? "message mine" : "message";

    const bubble = document.createElement("div");
    bubble.className = "bubble";
    bubble.textContent = message.text;

    row.appendChild(bubble);
    list.appendChild(row);
  });

  list.scrollTop = list.scrollHeight;
}

function sendMessage(event) {
  event.preventDefault();

  if (!currentRoom) return;

  const input = $("chatInput");
  const text = input.value.trim();

  if (!text) return;

  const key = "youthOnChat_" + currentRoom.id;
  const messages = readData(key);

  messages.push({
    text: text,
    mine: true
  });

  if (saveData(key, messages)) {
    input.value = "";
    renderMessages();
  }
}

const cooking = {
  "베이킹": [
    {
      emoji: "🍪",
      name: "초보 쿠키 만들기",
      people: 8,
      price: 5000,
      detail: "쿠키 반죽과 굽기의 기초"
    },
    {
      emoji: "🎂",
      name: "미니 케이크 꾸미기",
      people: 6,
      price: 8000,
      detail: "크림과 토핑으로 케이크 꾸미기"
    },
    {
      emoji: "🍞",
      name: "폭신한 빵 만들기",
      people: 5,
      price: 7000,
      detail: "반죽과 발효의 기초"
    }
  ],

  "양식": [
    {
      emoji: "🍝",
      name: "초보 파스타 클래스",
      people: 7,
      price: 6000,
      detail: "간단한 파스타 조리법"
    }
  ],

  "한식": [
    {
      emoji: "🍚",
      name: "한식 요리 기초",
      people: 6,
      price: 5000,
      detail: "친숙한 한식 요리 배우기"
    }
  ],

  "일식": [
    {
      emoji: "🍙",
      name: "주먹밥 만들기",
      people: 5,
      price: 4000,
      detail: "다양한 재료로 주먹밥 만들기"
    }
  ]
};

function showClasses(category) {
  $("classTitle").textContent = category + " 클래스";

  const list = $("classList");
  list.replaceChildren();

  cooking[category].forEach(item => {
    addItem(
      list,
      item.emoji,
      item.name,
      item.detail,
      [
        "👥 " + item.people + "명",
        "💰 " + item.price.toLocaleString("ko-KR") + "원"
      ],
      () => openLesson(item)
    );
  });

  go("classes");
}

function openLesson(item) {
  currentClass = item;

  $("lessonTitle").textContent = item.emoji + " " + item.name;

  $("lessonInfo").textContent =
    "참여 인원 " + item.people + "명 · 예시 가격 " +
    item.price.toLocaleString("ko-KR") + "원";

  $("videoUrl").value = "";

  go("lesson");
}

function openVideo() {
  const value = $("videoUrl").value.trim();

  if (!value) {
    alert("영상 주소를 먼저 입력해 주세요.");
    return;
  }

  try {
    const url = new URL(value);

    if (url.protocol !== "https:" && url.protocol !== "http:") {
      throw new Error("잘못된 주소");
    }

    window.open(url.href, "_blank", "noopener,noreferrer");
  } catch (error) {
    alert("올바른 영상 URL을 입력해 주세요.");
  }
}

function joinClass() {
  if (!currentClass) return;

  const saved = readData("youthOnClasses");

  if (saved.some(item => item.name === currentClass.name)) {
    alert("이미 내 클래스에 가입되어 있어요.");
    return;
  }

  saved.push(currentClass);

  if (saveData("youthOnClasses", saved)) {
    alert("내 클래스에 저장했어요!");
  }
}

renderRooms();
</script>

</body>
</html>
