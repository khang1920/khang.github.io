# khang- AePTON X EoBlox Executor 
 --- 

 const wait = (ms) => new Promise(resolve => setTimeout(resolve, ms));
let apiStatus = false; // Biến cờ theo dõi trạng thái API

async function startAPI() {
    while (apiStatus) {
        // Thay thế bằng hành động gọi API thực tế
        console.log("SendSummonRequest fired with value 5");
        await wait(1000);
    }
}

// Tạo nút button
const button = document.createElement('button');
button.textContent = 'Bật/Tắt API';

button.addEventListener('click', () => {
    apiStatus = !apiStatus;
    if (apiStatus) {
        button.textContent = 'Tắt API';
        startAPI();
    } else {
        button.textContent = 'Bật API';
    }
});

// Thêm nút vào DOM
document.body.appendChild(button);
