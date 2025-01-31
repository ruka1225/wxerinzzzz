// 방명록 메시지 추가 함수
function addMessage() {
    let name = document.getElementById("name").value;
    let message = document.getElementById("message").value;
    
    if (name === "" || message === "") {
        alert("이름과 메시지를 입력해주세요!");
        return;
    }

    let guestbookList = document.getElementById("guestbook-list");

    // 새로운 리스트 아이템 만들기
    let listItem = document.createElement("li");
    listItem.innerHTML = `<strong>${name}</strong>: ${message}`;

    // 리스트에 추가
    guestbookList.appendChild(listItem);

    // 입력칸 초기화
    document.getElementById("name").value = "";
    document.getElementById("message").value = "";

    // 메시지 저장
    saveMessages();
}

// 메시지를 로컬 저장소(localStorage)에 저장
function saveMessages() {
    let guestbookList = document.getElementById("guestbook-list").innerHTML;
    localStorage.setItem("guestbook", guestbookList);
}

// 페이지 로드 시 저장된 메시지 불러오기
function loadMessages() {
    let savedMessages = localStorage.getItem("guestbook");
    if (savedMessages) {
        document.getElementById("guestbook-list").innerHTML = savedMessages;
    }
}

// 페이지가 열릴 때 저장된 메시지 불러오기
window.onload = loadMessages;
