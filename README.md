<!DOCTYPE html>
<html>
<head>
    <title>데이터 입력</title>
    <script>
        document.getElementById("dataForm").addEventListener("submit", function (event) {
            event.preventDefault();

            const formData = new FormData(this);

            fetch("/submit", {
                method: "POST",
                body: formData,
            })
            .then(response => response.json())
            .then(data => {
                const feedback = document.getElementById("feedback");
                feedback.innerText = data.message || "Error: " + data.error;
            })
            .catch(() => {
                alert("An unexpected error occurred.");
            });
        });
    </script>
</head>
<body>
    <h1>사용자 및 반려동물 정보 입력</h1>
    <form id="dataForm" method="POST" action="/submit">
        <h2>사용자 정보</h2>
        <label for="name">이름:</label>
        <input type="text" id="name" name="name" required><br><br>

        <label for="age">나이:</label>
        <input type="number" id="age" name="age" min="0" required><br><br>

        <label for="address">주소:</label>
        <input type="text" id="address" name="address" required><br><br>

        <label for="email">이메일:</label>
        <input type="email" id="email" name="email" required><br><br>

        <h2>반려동물 정보</h2>
        <label for="pet_name">반려동물 이름:</label>
        <input type="text" id="pet_name" name="pet_name" required><br><br>

        <label for="pet_age">반려동물 나이:</label>
        <input type="number" id="pet_age" name="pet_age" min="0" required><br><br>

        <label for="pet_birthday">반려동물 생일:</label>
        <input type="date" id="pet_birthday" name="pet_birthday" required><br><br>

        <label for="pet_breed">반려동물 종:</label>
        <input type="text" id="pet_breed" name="pet_breed" required><br><br>

        <button type="submit">제출</button>
    </form>
    <p id="feedback"></p>
</body>
</html>
