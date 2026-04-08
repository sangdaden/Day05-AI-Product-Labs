# AI Product Canvas — `VinMec`: AI agent nhắc lịch tái khám thông minh

Điền theo case: **Bệnh nhân VinMec, đặc biệt là người cao tuổi, gặp khó khăn trong việc nhớ và đặt lịch tái khám trên app `MyVinMec`.**

---

## Canvas

|   | Value | Trust | Feasibility |
|---|-------|-------|-------------|
| **Câu hỏi guide** | User nào? Pain gì? AI giải quyết gì mà cách hiện tại không giải được? | Khi AI sai thì user bị ảnh hưởng thế nào? User biết AI sai bằng cách nào? User sửa bằng cách nào? | Cost bao nhiêu/request? Latency bao lâu? Risk chính là gì? |
| **Trả lời** | **User chính:** bệnh nhân VinMec, đặc biệt là người cao tuổi hoặc người bận rộn, cần tái khám định kỳ nhưng hay quên hoặc ngại thao tác trong app. **Pain:** dễ bỏ lỡ lịch tái khám, quên thời gian cần quay lại, không biết bác sĩ còn slot nào phù hợp, thao tác đặt lịch trên app chưa thuận tiện với người lớn tuổi. **AI giải quyết:** một AI agent trợ lý sức khỏe chủ động nhắc lịch tái khám đúng thời điểm, gợi ý bác sĩ/khung giờ phù hợp, tự kiểm tra slot, hỗ trợ đặt lịch nhanh và nhắc lại qua nhiều kênh như app/push/SMS/callbot. | **Nếu AI sai:** bệnh nhân có thể đặt nhầm lịch, nhắc sai ngày, bỏ lỡ lần tái khám quan trọng hoặc cảm thấy lo lắng, mất niềm tin. **User biết AI sai bằng cách:** xem thẻ xác nhận trước khi chốt lịch, đối chiếu với lịch khám trong app/SMS, hoặc phát hiện thông tin bác sĩ/giờ khám không đúng nhu cầu. **User sửa bằng cách:** bấm `Xác nhận lại`, `Đổi giờ`, `Đổi bác sĩ`, hoặc chuyển sang nhân viên CSKH/hotline. Hệ thống cần luôn có human fallback vì đây là domain y tế nhạy cảm. | **Cost:** mức trung bình thấp đến trung bình cho mỗi request vì phần lớn là reminder + checking slot + orchestration, không cần model quá nặng. **Latency:** reminder/gợi ý nên dưới 3 giây; kiểm tra slot và đặt lịch có thể chấp nhận 3–8 giây. **Risk chính:** sai lịch khám, lộ dữ liệu sức khỏe, gửi nhắc nhở sai người, hallucination về thông tin y khoa, và tích hợp khó với hệ thống đặt lịch/hospital backend. Cần ưu tiên bảo mật, consent và audit log. |

---

## Automation hay augmentation?

☐ Automation — AI làm thay, user không can thiệp  
☑ Augmentation — AI gợi ý, user quyết định cuối cùng

**Justify:**  
Bài toán này nên bắt đầu bằng **augmentation** vì liên quan tới sức khỏe và lịch khám thật. AI có thể **chủ động nhắc**, **đề xuất slot**, và thậm chí chuẩn bị sẵn booking flow, nhưng user vẫn nên là người **xác nhận cuối cùng** trước khi chốt lịch. Sau khi dữ liệu đủ tốt, có thể tăng dần mức tự động hóa cho các ca rủi ro thấp như tái khám định kỳ đơn giản.

---

## Learning signal

| # | Câu hỏi | Trả lời |
|---|---------|---------|
| 1 | User correction đi vào đâu? | Đi vào log sửa lịch: user đổi giờ nào, đổi bác sĩ nào, bỏ qua gợi ý nào, có xác nhận hay hủy sau khi AI nhắc không. Đây là dữ liệu để cải thiện logic gợi ý thời điểm nhắc và slot phù hợp. |
| 2 | Product thu signal gì để biết tốt lên hay tệ đi? | Tỷ lệ mở nhắc nhở, tỷ lệ xác nhận tái khám, tỷ lệ đặt lịch thành công, tỷ lệ bỏ lỡ lịch, tỷ lệ đổi/hủy sau khi AI đặt, phản hồi hài lòng từ bệnh nhân, và số ca phải escalte sang CSKH. |
| 3 | Data thuộc loại nào? ☐ User-specific · ☐ Domain-specific · ☐ Real-time · ☐ Human-judgment · ☐ Khác: ___ | **User-specific**, **Domain-specific**, **Real-time**, **Human-judgment**. Dữ liệu gồm lịch sử khám, specialty/bác sĩ đã khám, thời gian tái khám khuyến nghị, hành vi xác nhận/hủy lịch, và phản hồi của user. |

**Có marginal value không?** (Model đã biết cái này chưa? Ai khác cũng thu được data này không?)  
**Có.** Dữ liệu tái khám của bệnh nhân VinMec là dữ liệu rất đặc thù theo hệ thống, theo bác sĩ, theo chuyên khoa và theo hành vi thật của bệnh nhân. Đây không phải loại dữ liệu public model đã biết sẵn. Nếu thu được đủ feedback loop, VinMec có thể tạo lợi thế riêng về chất lượng nhắc tái khám và giảm no-show hiệu quả hơn đối thủ.

---

## Gợi ý user story ngắn

1. Là một bệnh nhân lớn tuổi, tôi muốn được nhắc tái khám đúng lúc để không quên lịch quan trọng.
2. Là một người bận rộn, tôi muốn AI gợi ý sẵn slot phù hợp để tôi không phải tự tìm nhiều bước trong app.
3. Là một bệnh nhân đang theo dõi bệnh mạn tính, tôi muốn được nhắc qua nhiều kênh để giảm nguy cơ bỏ lỡ tái khám.
4. Là người dùng thận trọng, tôi muốn luôn có bước xác nhận cuối cùng trước khi lịch được đặt chính thức.

---

## 4 paths UX ngắn cho case này

### 1. Khi AI đúng
- AI nhắc đúng thời điểm tái khám
- gợi ý đúng bác sĩ/chuyên khoa đã khám trước đó
- user bấm `Xác nhận` và đặt lịch nhanh trong ít bước

### 2. Khi AI không chắc
- AI nói rõ: **“Tôi chưa chắc bạn muốn bác sĩ cũ hay slot sớm nhất”**
- hiển thị 2–3 lựa chọn thay vì tự quyết
- yêu cầu xác nhận trước khi đặt

### 3. Khi AI sai
- user thấy ngay trên confirmation card là sai ngày/giờ/bác sĩ
- có nút `Đổi lịch`, `Chọn bác sĩ khác`, `Liên hệ hỗ trợ`
- không tự động chốt nếu thiếu xác nhận cuối

### 4. Khi user mất tin
- cho phép tắt AI nhắc lịch
- chuyển về flow đặt lịch thủ công truyền thống
- có hotline / CSKH hỗ trợ người thật

---

## One-line pitch

> **Một AI agent trợ lý sức khỏe trong `MyVinMec` giúp bệnh nhân — đặc biệt là người cao tuổi — không bỏ lỡ lịch tái khám bằng cách chủ động nhắc, kiểm tra slot, hỗ trợ đặt lịch và follow-up đa kênh một cách an toàn.**

---

*Canvas hoàn chỉnh cho bài tập nhóm / hackathon — VinMec follow-up care agent*