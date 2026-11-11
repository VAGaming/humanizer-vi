---
name: humanizer-vi
description: Rewrite Vietnamese text so it reads like a real Vietnamese person wrote it, removing the tells of AI-generated or machine-translated writing (sáo ngữ, văn dịch, lạm dụng từ Hán Việt, từ nối dày đặc, kết bài "Hy vọng bài viết hữu ích"...). Use when the user asks to humanize, "viết lại cho tự nhiên", "bớt giọng AI", "cho giống người viết", "sửa văn dịch", or to check whether a Vietnamese text sounds AI-written.
---

# Humanizer (Tiếng Việt)

Your job: take Vietnamese text that sounds AI-generated or translated from English, and rewrite it so it reads like a fluent Vietnamese writer produced it for this specific purpose. Keep the meaning, the facts, and the intended register. Do not add facts you don't have.

## Workflow

1. **Identify register first.** Is this a Facebook post, a blog/SEO article, an email to a boss, an academic essay, a product description, a chat message? Register decides pronouns (tôi / mình / em / chúng tôi), sentence particles, and how formal the vocabulary should be. If the user didn't say and it's ambiguous, keep the original register.
2. **Scan for the patterns below.** Note which ones appear.
3. **Rewrite.** Fix the patterns, but don't just swap words: restructure sentences, cut padding, vary rhythm, make claims concrete.
4. **Self-audit.** Reread your draft and ask: "Câu nào vẫn nghe như AI hoặc văn dịch?" Fix those, then stop. Don't over-polish into a new kind of artificial.
5. **Output** the rewritten text. Then, unless the user only wants the text, add a short list (3–6 bullets) of the main changes, in Vietnamese.

If the user only asks "does this sound AI?", give a verdict plus the specific patterns found with quotes, without rewriting.

## Patterns to remove

### 1. Mở bài sáo rỗng
AI opens with a grand context sentence that says nothing.
- "Trong thời đại công nghệ 4.0 ngày nay, ..."
- "Trong bối cảnh xã hội ngày càng phát triển, ..."
- "Có thể nói rằng / Không thể phủ nhận rằng ..."
- "Bạn đã bao giờ tự hỏi ...?"
- "Hãy cùng [tên trang] tìm hiểu / khám phá qua bài viết dưới đây nhé!"

**Fix:** start with the actual point, a concrete fact, or a specific situation.

### 2. Kết bài sáo rỗng và câu "chatbot"
- "Tóm lại, ...", "Nhìn chung, ...", "Tựu trung lại, ...", "Khép lại, ..."
- "Hy vọng bài viết trên đã mang đến cho bạn những thông tin hữu ích."
- "Chúc bạn thành công!", "Nếu có bất kỳ thắc mắc nào, đừng ngần ngại liên hệ ..."
- "Chắc chắn rồi!", "Câu hỏi rất hay!", "Dưới đây là ...", "Là một mô hình ngôn ngữ AI ..."

**Fix:** delete. End where the content ends, or with one sentence that adds something (a next step, an opinion, a specific caveat).

### 3. Từ ngữ thổi phồng, khẩu hiệu
"đóng vai trò quan trọng / then chốt / không thể thiếu", "là chìa khóa", "mở ra cánh cửa", "hành trình", "bức tranh toàn cảnh", "nâng tầm", "khai phá tiềm năng", "bứt phá", "đột phá", "vô cùng", "cực kỳ", "tuyệt vời", "hoàn hảo", "trải nghiệm đỉnh cao", "góp phần to lớn", "một trong những ... nhất".

**Fix:** replace with what it actually does, with numbers or examples if the source has them. "Vitamin D đóng vai trò vô cùng quan trọng đối với sức khỏe" → "Thiếu vitamin D thì xương dễ giòn, nhất là ở người già."

### 4. Văn dịch từ tiếng Anh (calque)
| AI / văn dịch | Tự nhiên hơn |
|---|---|
| "Điều quan trọng cần lưu ý là ..." (It's important to note) | bỏ, hoặc "Lưu ý:" |
| "Khi nói đến X, ..." (When it comes to) | "Về X, ..." hoặc nói thẳng |
| "... được thực hiện bởi ..." (passive "by") | đổi sang chủ động: "A làm B" |
| "một cách hiệu quả / nhanh chóng / dễ dàng" (adverb -ly) | "làm hiệu quả", "nhanh", hoặc bỏ |
| "Nó" chỉ sự vật, ý tưởng trừu tượng | lặp lại danh từ, hoặc bỏ chủ ngữ |
| "Việc ... là rất cần thiết" | "Cần ..." / "Nên ..." |
| "sở hữu" (possess) cho mọi thứ | "có" |
| "đến từ" (comes from) cho thương hiệu, người | "của", "người [quê]" |
| "Điều này giúp ..." mở đầu câu liên tục | nối vào câu trước, hoặc chủ ngữ cụ thể |
| chuỗi "của": "sự phát triển của ngành công nghiệp của Việt Nam" | rút gọn: "ngành công nghiệp Việt Nam phát triển" |
| "Đáng chú ý là ...", "Thú vị là ..." | bỏ, để chi tiết tự gây chú ý |

### 5. Lạm dụng từ Hán Việt, động từ rỗng
"sử dụng" → "dùng", "thực hiện việc ..." → động từ chính, "tiến hành" → bỏ, "nhằm mục đích" → "để", "gia tăng" → "tăng", "trong quá trình" → "khi", "tuy nhiên" (lặp) → "nhưng", "hiện nay" (lặp) → bỏ, "cung cấp / mang lại / đảm bảo" (khi không có nghĩa cụ thể) → nói rõ cái gì.

Keep Hán Việt where the register needs it (văn bản hành chính, học thuật). The tell is density, not any single word.

### 6. Từ nối dày đặc
Paragraphs that start with "Bên cạnh đó", "Ngoài ra", "Hơn nữa", "Đặc biệt", "Chính vì vậy", "Do đó", "Không chỉ ... mà còn ..." in sequence.

**Fix:** cut most of them. Vietnamese flows fine with plain juxtaposition. Keep a connector only where the logical relation isn't obvious.

### 7. Cấu trúc đều đặn, máy móc
- Groups of exactly three ("nhanh chóng, tiện lợi và hiệu quả") everywhere.
- Every sentence the same length and shape.
- Every section: one intro sentence, three bullets, one wrap-up sentence.
- Bullet lists with a **bolded label:** followed by an explanation, when prose would do.

**Fix:** vary sentence length (some very short). Use two items or four. Turn lists into prose when the items are connected.

### 8. Rào đón, nước đôi
"có thể", "phần nào", "ở một mức độ nào đó", "tùy thuộc vào nhiều yếu tố", "mỗi người sẽ có lựa chọn riêng", "không có câu trả lời đúng hay sai".

**Fix:** commit to a claim when the source supports one. Keep one hedge where uncertainty is real.

### 9. Chung chung, thiếu chi tiết
"nhiều người cho rằng", "các chuyên gia khuyên", "nghiên cứu chỉ ra", "mang lại nhiều lợi ích", "phù hợp với mọi đối tượng".

**Fix:** use the specific person, number, place, or example if the text or the user provides it. If not, cut the vague claim or flag it to the user ("[cần nguồn]") rather than inventing one.

### 10. Hình thức không giống người Việt viết
- **Title Case kiểu Anh** trong tiêu đề: "Lợi Ích Của Việc Uống Nước" → "Lợi ích của việc uống nước" (tiếng Việt chỉ viết hoa chữ đầu và tên riêng). Exception: if the user's site style uses title case on purpose, keep it.
- **Dấu gạch ngang dài (—)** chèn giữa câu: rare in Vietnamese. Use dấu phẩy, dấu hai chấm, hoặc ngoặc đơn.
- **Số và ngày kiểu Anh:** "1,000,000 đồng" → "1.000.000 đồng" (hoặc "1 triệu đồng"); "3.5%" → "3,5%"; "12/25/2026" → "25/12/2026".
- **Emoji, in đậm** rải khắp đoạn văn.
- Dấu ngoặc kép thông minh lẫn lộn, khoảng trắng trước dấu câu ("đẹp !").

### 11. Giọng và xưng hô
- Pronouns that drift (bạn → quý khách → các bạn) or don't fit the relationship.
- Casual registers (mạng xã hội, tin nhắn, blog cá nhân) that have zero sentence particles. Real casual Vietnamese uses "nhé, nha, đấy, mà, chứ, thôi, cơ, á" naturally. Add a few where they fit; don't sprinkle them on every sentence.
- No opinion or personal angle at all in a text that is supposed to be personal. If the user's own voice is available (earlier messages, a sample), match it.
- Don't force slang, teen code, or regional dialect unless the user asks for it.

## Ví dụ

**Trước (AI):**
> Trong thời đại công nghệ 4.0 ngày nay, việc học tiếng Anh đóng vai trò vô cùng quan trọng và không thể thiếu. Tiếng Anh không chỉ giúp bạn mở ra cánh cửa cơ hội việc làm mà còn giúp bạn tiếp cận kho tri thức khổng lồ của nhân loại. Bên cạnh đó, việc sử dụng tiếng Anh một cách thành thạo còn giúp bạn tự tin hơn khi giao tiếp. Hãy cùng khám phá những phương pháp học tiếng Anh hiệu quả qua bài viết dưới đây nhé!

**Sau:**
> Biết tiếng Anh thì tìm việc dễ hơn hẳn, nhất là ở các công ty nước ngoài, nơi CV tiếng Anh gần như là điều kiện tối thiểu. Đọc tài liệu chuyên ngành cũng nhanh hơn vì không phải chờ bản dịch. Bài này tổng hợp vài cách học mà mình thấy hiệu quả với người đi làm, ít thời gian.

**Trước (văn dịch):**
> Điều quan trọng cần lưu ý là sản phẩm này được thiết kế bởi đội ngũ kỹ sư đến từ Nhật Bản. Nó sở hữu khả năng chống nước một cách hiệu quả.

**Sau:**
> Sản phẩm do kỹ sư Nhật thiết kế, chống nước tốt.

**Trước (email công việc, AI):**
> Kính gửi anh, em xin phép được gửi đến anh báo cáo tiến độ dự án. Hy vọng báo cáo này sẽ cung cấp cho anh cái nhìn tổng quan về tình hình hiện tại. Nếu anh có bất kỳ thắc mắc nào, xin đừng ngần ngại liên hệ với em.

**Sau:**
> Em gửi anh báo cáo tiến độ dự án. Anh xem giúp em, có gì chưa rõ anh cứ hỏi nhé.

## Rules

- Never change facts, numbers, names, or quotes. Never invent sources, statistics, or anecdotes.
- Keep the length roughly the same or shorter. Humanizing usually cuts 10–40%.
- Keep the user's register and pronoun choice unless they ask to change it.
- If the text has legal, medical, or technical terms, keep them exact.
- Don't announce "Đây là phiên bản đã được viết lại một cách tự nhiên hơn" — that line is itself an AI tell. Just give the text.
