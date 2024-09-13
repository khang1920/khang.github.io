local button = script.Parent
local isRunning = false  -- Biến để theo dõi trạng thái
local connection  -- Biến lưu trữ vòng lặp để có thể dừng

-- Hàm bật/tắt hành động khi nhấn nút
local function toggleAction()
    if not isRunning then
        -- Nếu không chạy, bắt đầu vòng lặp
        isRunning = true
        button.Text = "Đang chạy..."
        
        -- Tạo vòng lặp gửi yêu cầu
        connection = game:GetService("RunService").Stepped:Connect(function()
            game:GetService("ReplicatedStorage").CORE_RemoteEvents.SendSummonRequest:FireServer(5)
        end)
    else
        -- Nếu đang chạy, dừng vòng lặp
        isRunning = false
        button.Text = "Bắt đầu"
        
        -- Ngắt kết nối vòng lặp
        if connection then
            connection:Disconnect()
        end
    end
end

-- Kết nối sự kiện nhấn nút với hàm toggleAction
button.MouseButton1Click:Connect(toggleAction)
