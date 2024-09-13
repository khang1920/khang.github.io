<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Toggle Roblox API</title>
    <style>
        .toggle-button {
            padding: 10px 20px;
            font-size: 16px;
            background-color: lightgray;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }

        .on {
            background-color: green;
            color: white;
        }

        .off {
            background-color: red;
            color: white;
        }
    </style>
</head>
<body>

    <button id="toggleButton" class="toggle-button off">Tắt API</button>

    <script>
        // Biến để giữ trạng thái của API (bật/tắt)
        let isApiOn = false;

        // Hàm gửi yêu cầu đến API
        function callRobloxApi(state) {
            // Ở đây bạn cần thay thế URL của API Roblox vào
            const apiUrl = "https://roblox-api-endpoint.example.com"; // Thay bằng URL API Roblox của bạn

            // Tạo yêu cầu tới API (sử dụng phương thức fetch)
            fetch(apiUrl, {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json'
                },
                body: JSON.stringify({ apiState: state })  // Gửi trạng thái bật/tắt tới API
            })
            .then(response => response.json())
            .then(data => console.log(data))
            .catch(error => console.error('Error:', error));
        }

        // Lấy nút button từ DOM
        const toggleButton = document.getElementById('toggleButton');

        // Lắng nghe sự kiện nhấn nút
        toggleButton.addEventListener('click', function() {
            // Đổi trạng thái
            isApiOn = !isApiOn;

            // Cập nhật giao diện của nút
            if (isApiOn) {
                toggleButton.classList.remove('off');
                toggleButton.classList.add('on');
                toggleButton.textContent = 'Bật API';
            } else {
                toggleButton.classList.remove('on');
                toggleButton.classList.add('off');
                toggleButton.textContent = 'Tắt API';
            }

            // Gọi hàm để gửi yêu cầu đến API với trạng thái mới
            callRobloxApi(isApiOn);
        });
    </script>

</body>
</html>
