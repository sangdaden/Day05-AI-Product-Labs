# Phân tích UX sản phẩm AI thật — `V-App` / `V-AI`

## 1) Sản phẩm đã chọn

- **Sản phẩm:** `V-App — Trợ lý ảo V-AI`
- **AI feature:** trợ lý `text`, gợi ý theo context
- **Use case thử:** nhập câu lệnh text kiểu: **“Nhắc tôi 7 giờ tối gọi xe đi nhậu”**

---

## 2) Trước khi dùng: sản phẩm hứa gì?

Qua cách mô tả sản phẩm, `V-AI` được định vị như một **trợ lý ảo trong app** giúp người dùng:

- hỏi bằng ngôn ngữ tự nhiên thay vì tự mò menu
- kỳ vọng có thể tương tác tự nhiên như chat assistant, ít nhất bằng **text**, và có thể mở rộng sang `voice` trong tương lai
- nhận **gợi ý theo ngữ cảnh** để đi nhanh tới tính năng phù hợp
- giảm số bước thao tác, làm trải nghiệm “thông minh hơn”

### Kỳ vọng mà marketing tạo ra
1. User có thể hỏi như đang chat với người thật.
2. AI hiểu đúng ý kể cả khi câu hỏi hơi mơ hồ.
3. AI không chỉ trả lời mà còn **hỗ trợ user đi tới hành động đúng**.

---

## 3) Dùng thử: quan sát nhanh

- Trong trải nghiệm dùng thử của mình, mình **không thấy tính năng voice hoạt động / không thấy cho dùng voice**.
- Tương tác thực tế chủ yếu là qua **text** trong giao diện assistant.
- Khi mình nhập đúng câu **“Nhắc tôi 7 giờ tối gọi xe đi nhậu”**, `V-AI` phản hồi theo kiểu: **“V-AI hiện không thể thiết lập nhắc nhở trực tiếp. Tuy nhiên ...”**.
- Điều này cho thấy hiện tại AI **chưa thực sự thực thi được action** tạo reminder, mà mới dừng ở mức trả lời/gợi ý bằng text.
- Điểm tốt là hệ thống **không tự làm sai** một hành động quan trọng khi chưa có khả năng hỗ trợ.

---

## 4) Phân tích theo framework `4 paths`

| Path | Quan sát | Đánh giá |
|------|----------|----------|
| **1. Khi AI đúng** | Với các câu hỏi thông tin đơn giản, AI có thể trả lời bằng text khá an toàn và lịch sự. User nhận được hướng dẫn chung nhưng chưa chắc hoàn thành tác vụ ngay trong app. | **Tạm ổn**, nhưng value còn hạn chế. |
| **2. Khi AI không chắc** | Với câu lệnh như **“Nhắc tôi 7 giờ tối gọi xe đi nhậu”**, hệ thống không cố đoán mà trả lời rằng hiện chưa thể thiết lập nhắc nhở trực tiếp. Đây là một cách từ chối an toàn nhưng chưa thật sự thông minh. | **Trung bình**: an toàn nhưng chưa hữu ích. |
| **3. Khi AI sai / không làm được** | Khi user muốn một action cụ thể, AI không thực hiện được mà chỉ trả lời fallback. User vẫn phải tự mở app khác hoặc tự nhớ việc đó. | **Yếu nhất** vì thất bại ở đúng value mà user mong chờ. |
| **4. Khi user mất tin** | Sau khi bị từ chối một yêu cầu rất cơ bản như tạo reminder, user dễ kết luận rằng AI chỉ “nói chuyện” chứ chưa giúp làm việc thật. Fallback manual có, nhưng trải nghiệm tạo cảm giác hụt hẫng. | **Yếu** vì trust giảm nhanh. |

---

## 5) Nhận xét chính

### Path mà sản phẩm xử lý tốt nhất
**Path 2 — khi AI không làm được / không chắc** lại là path ổn nhất trong case này.

**Vì sao?**
- hệ thống **không bịa** là mình làm được reminder
- AI từ chối khá an toàn thay vì tạo một nhắc nhở sai
- đây là một dạng graceful failure cơ bản

### Path yếu nhất
**Path 3 — khi user muốn AI làm thật một action** là path yếu nhất.

**Vì sao?**
- user đưa ra một yêu cầu rất tự nhiên nhưng AI không thực thi được
- trải nghiệm dừng ở mức trả lời text, không tạo ra outcome thực sự
- user vẫn phải tự làm thủ công nên giá trị sản phẩm bị giảm mạnh

---

## 6) Gap giữa marketing và thực tế

### Marketing hứa
- trợ lý ảo hiểu ngữ cảnh
- hỏi tự nhiên, ra đúng hành động
- app trở nên thông minh và cá nhân hơn

### Thực tế dùng thử
- AI **trả lời được bằng text** và có thái độ an toàn
- nhưng với yêu cầu cụ thể như tạo `reminder`, hệ thống nói rõ là **chưa thể thiết lập trực tiếp**
- vì vậy trải nghiệm hiện tại giống một **chat assistant tư vấn**, chưa phải một **action assistant**

### Gap nằm ở đâu?
> `Marketing tạo cảm giác đây là một trợ lý ảo thông minh trong app, nhưng trải nghiệm thực tế vẫn nghiêng về hỏi-đáp hơn là làm việc trực tiếp cho user.`

Nói cách khác: khoảng cách lớn nhất nằm ở chỗ **user mong AI làm được việc**, còn hiện tại AI chủ yếu **giải thích hoặc từ chối lịch sự**.

---

## 7) Sketch “làm tốt hơn”

### Path chọn để cải thiện
Chọn **Path 3 — khi user muốn AI làm một action nhưng hệ thống chưa làm được**.

### A. `As-is` (bên trái)
Luồng hiện tại theo trải nghiệm thật:

1. User nhập text: **“Nhắc tôi 7 giờ tối gọi xe đi nhậu”**
2. AI hiểu đây là yêu cầu tạo nhắc nhở
3. `V-AI` trả lời: **“V-AI hiện không thể thiết lập nhắc nhở trực tiếp. Tuy nhiên ...”**
4. User không đạt được mục tiêu ban đầu
5. User phải tự chuyển sang cách làm thủ công

**Đánh dấu chỗ gãy:**
- AI hiểu ý định nhưng **không hoàn thành action**
- fallback mới dừng ở mức trả lời text
- trải nghiệm bị ngắt giữa chừng, không có outcome thật

### B. `To-be` (bên phải)
Luồng đề xuất dựa trên sketch của em:

#### Sketch 1 — `Text input + NLU phân tích`
Sau khi user nhập: **“Nhắc tôi 7 giờ tối gọi xe đi nhậu”**, AI tách ra:
- `time`: 7 giờ tối
- `service`: `Xanh SM` / gọi xe
- `action`: reminder

#### Sketch 2 — `Confirmation Card`
Nếu còn mơ hồ, hệ thống hiện thẻ xác nhận:

**Bạn muốn nhắc vào:**
1. `19:00 hôm nay`
2. `19:00 ngày mai`

**Bạn muốn làm gì?**
1. `Gọi Xanh SM`
2. `Đặt xe đi nhậu`
3. `Khác / chỉnh lại`

- CTA rõ: **`Xác nhận`**

#### Sketch 3 — `Smart Reminder + Context`
Sau khi user xác nhận, app mới tạo reminder:
- `19:00 hôm nay`
- `Gọi: Xanh SM`
- `Nguồn: từ text command`
- tùy chọn: **`Bật notification ưu tiên`**

=> Phần **thêm bối cảnh** giúp tăng độ rõ ràng và tăng `trust`.

### C. Thêm gì? Bớt gì? Đổi gì?

**Thêm:**
- lớp `NLU phân tích intent`
- `confirmation card` khi chưa chắc
- context trong reminder đã tạo
- tùy chọn `bật notification ưu tiên`

**Bớt:**
- việc AI tự tạo reminder ngay khi còn mơ hồ

**Đổi:**
- từ `tạo nhắc việc ngay` sang `xác nhận rồi mới tạo`

---

## 8) Vì sao phương án này tốt hơn?

- giảm nguy cơ user đi sai flow ngay từ đầu
- giảm số bước recovery khi AI hiểu sai
- tăng trust vì hệ thống **trung thực về uncertainty**
- phù hợp đúng tinh thần thiết kế AI product: không chỉ tối ưu lúc đúng, mà phải thiết kế tốt cả lúc không chắc và lúc sai

---

## 9) Bài nói 30 giây để share với nhóm

> “Em chọn `V-App` với case tạo reminder bằng text, vì khi dùng thử em không thấy app cho dùng voice. Khi em nhập đúng câu ‘Nhắc tôi 7 giờ tối gọi xe đi nhậu’, `V-AI` trả lời là hiện chưa thể thiết lập nhắc nhở trực tiếp. Nghĩa là AI hiểu được ý định nhưng chưa làm được action thật, nên user vẫn phải quay lại cách thủ công. Sketch của em đề xuất thêm bước `NLU + confirmation card`, sau đó cho phép tạo `smart reminder` có context để biến trải nghiệm từ hỏi-đáp sang hỗ trợ hành động thực sự.”
---

## Kết luận ngắn

`V-App / V-AI` cho thấy giá trị rõ ở **happy path**, nhưng còn yếu ở **uncertainty path**. Nếu cải thiện cách hệ thống báo “không chắc”, đưa alternatives và fallback rõ ràng hơn, trải nghiệm sẽ đáng tin và đúng với lời hứa marketing hơn nhiều.