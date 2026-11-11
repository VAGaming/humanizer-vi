---
name: humanizer-vi
description: Rewrite Vietnamese text so it reads like a real Vietnamese person wrote it, removing the tells of AI-generated or machine-translated writing (sáo ngữ, văn dịch, lạm dụng từ Hán Việt, từ nối dày đặc, kết bài "Hy vọng bài viết hữu ích"...). Use when the user asks to humanize, "viết lại cho tự nhiên", "bớt giọng AI", "cho giống người viết", "sửa văn dịch", or to check whether a Vietnamese text sounds AI-written.
---

# Humanizer (Tiếng Việt)

Your job: take Vietnamese text that sounds AI-generated or translated from English, and rewrite it so it reads like a fluent Vietnamese writer produced it for this specific purpose. Keep every claim, fact, and the intended register. Do not add facts you don't have.

## Workflow

1. **Identify register.** Facebook post, blog/SEO article, email to a boss, academic essay, product description, chat message? Register decides pronouns (tôi / mình / em / chúng tôi), sentence particles, and how formal the vocabulary should be. If ambiguous, keep the original register.
2. **Calibrate voice.** If the user gave a sample of their own writing (now or earlier in the conversation), match its sentence length, word choice, pronouns, particles, and punctuation. The sample overrides the general rules below: if the user writes with dashes or Hán Việt, keep them. Without a sample: personal writing keeps opinions and asides; technical or formal writing stays neutral.
3. **Mark the tells**, strongest first. Each pattern below is tagged:
   - **[Mạnh]**: one occurrence is enough to justify a fix.
   - **[Yếu]**: only a problem when several weak tells cluster in the same passage. A single "tuy nhiên" or one Hán Việt word is normal Vietnamese; leave it.
4. **Draft** a rewrite. Restructure sentences, cut padding, vary rhythm, make claims concrete. Keep every claim from the source. You may add a specific detail only if the user or the source provides it.
5. **Critique the draft.** Check: (a) Did any fact, number, name, or claim get lost or changed? (b) Which tells survived? Ask "Câu nào vẫn nghe như AI hoặc văn dịch?" (c) Did the rewrite become artificial in a new way (forced slang, too many particles)?
6. **Write the final version**, fixing what the critique found. Then stop. Don't over-polish.

If the user only asks "does this sound AI?", give a verdict plus the specific patterns found with quotes, ranked strongest first, without rewriting.

## Output format

**Pasted text** (default):

```
**Bản nháp**
<draft>

**Còn sót**
- <tells still present in the draft, or "Không còn">

**Bản cuối**
<final text>

**Đã sửa**
- <3–6 bullets in Vietnamese: the main changes>
```

If the user asks for just the text ("chỉ cần bản sửa", "đưa mỗi kết quả"), give only the final version.

**File mode** (the user points at a file): edit only the prose in place. Leave code blocks, commands, file paths, URLs, links, YAML/frontmatter, and HTML tags untouched. Report how many sections you rewrote and which you left alone.

## Patterns

### 1. Mở bài sáo rỗng [Mạnh]
AI opens with a grand context sentence that says nothing.
- "Trong thời đại công nghệ 4.0 ngày nay, ...", "Trong kỷ nguyên số, ...", "Trong thế giới ngày nay, ..."
- "Trong bối cảnh xã hội ngày càng phát triển, ..."
- "Có thể nói rằng / Không thể phủ nhận rằng / Thật vậy, ..."
- "Bạn đã bao giờ tự hỏi ...?"
- "Hãy cùng [tên trang] tìm hiểu / khám phá / đi sâu vào ... qua bài viết dưới đây nhé!"

**Fix:** start with the actual point, a concrete fact, or a specific situation.

### 2. Kết bài sáo rỗng và câu "chatbot" [Mạnh]
- "Tóm lại (là), ...", "Nhìn chung, ...", "Tựu trung lại, ...", "Khép lại, ..."
- "Hy vọng bài viết trên đã mang đến cho bạn những thông tin hữu ích."
- "Chúc bạn thành công!", "Nếu có bất kỳ thắc mắc nào, đừng ngần ngại liên hệ ..."
- "Chắc chắn rồi!", "Câu hỏi rất hay!", "Dưới đây là ...", "Là một mô hình ngôn ngữ AI ...", "Tính đến thời điểm dữ liệu của tôi ..."

**Fix:** delete. End where the content ends, or with one sentence that adds something (a next step, an opinion, a specific caveat).

### 3. Tự mô tả, nói lại điều đã nói [Mạnh]
- The text describes itself: "Bài viết này sẽ trình bày ...", "Trong phần tiếp theo, chúng ta sẽ ...", "Như đã đề cập ở trên, ..."
- The ending restates the body in different words.
- A heading followed by a sentence that repeats the heading.
- In a reply, re-explaining context the reader already knows.

**Fix:** cut. Say the thing instead of announcing it.

### 4. Cấu trúc "Không chỉ ... mà còn ..." và dàn dựng [Mạnh]
- "Không chỉ ... mà còn ...", "Không phải là X, mà là Y", "X không đơn thuần là ..., mà còn là ..."
- Staged run-ups: "Và đây chính là điều ...", "Điều thú vị là gì? Đó là ..."
- Arguing against a claim nobody made.
- One-line "deep" closers: "Bởi suy cho cùng, ... chính là ..."

**Fix:** state the point directly. "Tiếng Anh không chỉ giúp tìm việc mà còn giúp đọc tài liệu" → "Biết tiếng Anh thì dễ tìm việc, đọc tài liệu cũng nhanh hơn."

### 5. Từ ngữ thổi phồng, khẩu hiệu [Mạnh nếu dày, Yếu nếu lẻ tẻ]
- Cụm vai trò: "đóng vai trò quan trọng / then chốt / không thể thiếu", "là chìa khóa", "yếu tố then chốt", "góp phần to lớn", "góp phần tạo dựng"
- Tính từ: "toàn diện", "sâu sắc", "vượt trội", "hoàn hảo", "tối ưu", "vô cùng", "cực kỳ", "tuyệt vời", "đỉnh cao"
- Động từ vĩ mô: "khám phá", "nâng tầm", "mở ra (cánh cửa)", "đi sâu vào", "giải mã", "trang bị", "khai phá tiềm năng", "bứt phá"
- Hình ảnh sáo: "hành trình", "bức tranh toàn cảnh", "một trong những ... nhất"

**Fix:** replace with what it actually does, using numbers or examples from the source.
- "Vitamin D đóng vai trò vô cùng quan trọng đối với sức khỏe" → "Thiếu vitamin D thì xương dễ giòn, nhất là ở người già."
- "Nâng cao hiệu suất" → "Làm việc nhanh hơn"
- "Yếu tố then chốt" → "Điều quan trọng nhất"
- "Cung cấp trải nghiệm tối ưu" → "Dùng sướng hơn" (casual) / "Dùng thuận tiện hơn" (neutral)

### 6. Văn dịch từ tiếng Anh (calque) [Mạnh]
| AI / văn dịch | Tự nhiên hơn |
|---|---|
| "Điều quan trọng cần lưu ý là ..." (It's important to note) | bỏ, hoặc "Lưu ý:" |
| "Tuy nhiên, điều quan trọng cần nhớ là ..." | bỏ, nói thẳng điều cần nhớ |
| "Khi nói đến X, ..." (When it comes to) | "Về X, ..." hoặc nói thẳng |
| "... được thực hiện bởi ..." (passive "by") | đổi sang chủ động: "A làm B" |
| "một cách hiệu quả / nhanh chóng / dễ dàng" (adverb -ly) | "làm hiệu quả", "nhanh", hoặc bỏ |
| "Nó" chỉ sự vật, ý tưởng trừu tượng | lặp lại danh từ, hoặc bỏ chủ ngữ |
| "Việc ... là rất cần thiết" | "Cần ..." / "Nên ..." |
| "sở hữu" (possess) cho mọi thứ | "có" |
| "đến từ" (comes from) cho thương hiệu, người | "của", "người [quê]" |
| "Điều này giúp ..." mở đầu câu liên tục | nối vào câu trước, hoặc chủ ngữ cụ thể |
| chuỗi "của": "sự phát triển của ngành công nghiệp của Việt Nam" | "ngành công nghiệp Việt Nam phát triển" |
| "Đáng chú ý là ...", "Thú vị là ..." | bỏ, để chi tiết tự gây chú ý |

### 7. Câu dài kiểu Tây, từ nối dày đặc [Yếu]
- Long sentences stitched together with "đồng thời", "tuy nhiên", "mặt khác", "bên cạnh đó", "hơn nữa", "hơn thế nữa", "ngoài ra", "do đó", "chính vì vậy".
- Consecutive paragraphs each opening with a connector.

**Fix:** split into shorter sentences; some can be very short. Vietnamese flows fine with plain juxtaposition. Keep a connector only where the logical relation isn't obvious.

### 8. Lạm dụng từ Hán Việt, động từ rỗng [Yếu]
"sử dụng" → "dùng", "thực hiện việc ..." → động từ chính, "tiến hành" → bỏ, "nhằm mục đích" → "để", "gia tăng" → "tăng", "trong quá trình" → "khi", "tối ưu hóa" → "làm tốt hơn", "trải nghiệm" → "cảm giác" / "dùng thử", "giá trị tinh thần to lớn" → nói cụ thể giá trị gì, "cung cấp / mang lại / đảm bảo" (khi không có nghĩa cụ thể) → nói rõ cái gì.

Keep Hán Việt where the register needs it (văn bản hành chính, học thuật, pháp lý). The tell is density, not any single word.

### 9. Cấu trúc đều đặn, máy móc [Yếu]
- Groups of exactly three ("nhanh chóng, tiện lợi và hiệu quả") everywhere.
- Every sentence and paragraph the same length and shape.
- Every section: one intro sentence, three bullets, one wrap-up sentence.
- Bullet lists with a **bolded label:** followed by an explanation, when prose would do.
- The same keyword repeated in every sentence (often SEO text).

**Fix:** vary sentence and paragraph length. Use two items or four. Turn connected list items into prose. Replace repeated keywords with "nó", "cái này", a synonym, or by dropping the subject (Vietnamese allows it).

### 10. Rào đón, nước đôi [Yếu]
"có thể", "phần nào", "ở một mức độ nào đó", "tùy thuộc vào nhiều yếu tố", "mỗi người sẽ có lựa chọn riêng", "không có câu trả lời đúng hay sai".

**Fix:** commit to a claim when the source supports one. Keep one hedge where uncertainty is real.

### 11. Chung chung, thiếu chi tiết [Yếu]
"nhiều người cho rằng", "các chuyên gia khuyên", "nghiên cứu chỉ ra", "mang lại nhiều lợi ích", "phù hợp với mọi đối tượng", industry filler like "tối ưu danh mục" (tài chính), "chăm sóc toàn diện" (y tế).

**Fix:** use the specific person, number, place, or example if the text or the user provides it. If not, cut the vague claim or flag it ("[cần nguồn]") rather than inventing one.

### 12. Hình thức không giống người Việt viết [Yếu]
- **Title Case kiểu Anh** trong tiêu đề: "Lợi Ích Của Việc Uống Nước" → "Lợi ích của việc uống nước". Exception: if the user's site style uses title case on purpose, keep it.
- **Dấu gạch ngang dài (—)** chèn giữa câu: rare in Vietnamese. Use dấu phẩy, dấu hai chấm, ngoặc đơn, or a plain "-".
- **Số và ngày kiểu Anh:** "1,000,000 đồng" → "1.000.000 đồng" / "1 triệu đồng"; "3.5%" → "3,5%"; "12/25/2026" → "25/12/2026".
- **Emoji, in đậm** rải khắp đoạn văn; decorative headings on short texts.
- Khoảng trắng trước dấu câu ("đẹp !").
- Don't treat straight vs curly quotes as a tell; Vietnamese writers use both.

### 13. Giọng, xưng hô, văn hóa [Mạnh nếu sai quan hệ, Yếu nếu chỉ khô]
- **Wrong relationship:** "bạn" for readers or recipients clearly over ~40 or senior (use "anh/chị", "cô/chú"); "Tôi rất vui được gửi ..." in an email to a boss (use "Em xin gửi ..." / "Em gửi anh ...").
- **Drifting pronouns:** bạn → quý khách → các bạn in one text.
- **Cultural slips:** "tết Việt Nam" → "Tết" / "Tết Nguyên đán"; holidays, food, places, and titles named the way a foreigner would.
- **No particles in casual text:** social posts, chat, personal blogs with zero "nhé, nha, đấy, mà, chứ, thôi, cơ, á". Add a few where they fit, not on every sentence.
- **No personal angle** in a text meant to be personal: Wikipedia/textbook tone in a review or status post. Turn it into short first-person lines with opinions.
- Don't force slang, teen code, or regional dialect unless the user asks or their sample uses it.

## Ví dụ

**Trước (AI):**
> Trong thời đại công nghệ 4.0 ngày nay, việc học tiếng Anh đóng vai trò vô cùng quan trọng và không thể thiếu. Tiếng Anh không chỉ giúp bạn mở ra cánh cửa cơ hội việc làm mà còn giúp bạn tiếp cận kho tri thức khổng lồ của nhân loại. Bên cạnh đó, việc sử dụng tiếng Anh một cách thành thạo còn giúp bạn tự tin hơn khi giao tiếp. Hãy cùng khám phá những phương pháp học tiếng Anh hiệu quả qua bài viết dưới đây nhé!

**Sau:**
> Biết tiếng Anh thì tìm việc dễ hơn hẳn. Đọc tài liệu cũng nhanh hơn vì không phải chờ bản dịch, nói chuyện với người nước ngoài cũng đỡ ngại. Bài này tổng hợp vài cách học hiệu quả.

**Trước (văn dịch):**
> Điều quan trọng cần lưu ý là sản phẩm này được thiết kế bởi đội ngũ kỹ sư đến từ Nhật Bản. Nó sở hữu khả năng chống nước một cách hiệu quả.

**Sau:**
> Sản phẩm do kỹ sư Nhật thiết kế, chống nước tốt.

**Trước (email công việc, AI):**
> Kính gửi anh, tôi rất vui được gửi đến anh báo cáo tiến độ dự án. Hy vọng báo cáo này sẽ cung cấp cho anh cái nhìn tổng quan về tình hình hiện tại. Nếu anh có bất kỳ thắc mắc nào, xin đừng ngần ngại liên hệ với tôi.

**Sau:**
> Em gửi anh báo cáo tiến độ dự án. Anh xem giúp em, có gì chưa rõ anh cứ hỏi nhé.

**Trước (review quán ăn, giọng Wikipedia):**
> Nhà hàng sở hữu không gian ấm cúng, góp phần tạo dựng trải nghiệm ẩm thực đáng nhớ cho thực khách.

**Sau:**
> Quán nhỏ mà ấm cúng, ngồi lâu không thấy chán.

## Rules

- Never change facts, numbers, names, or quotes. Never invent sources, statistics, or anecdotes.
- Keep the length roughly the same or shorter. Humanizing usually cuts 10–40%.
- Keep the user's register and pronoun choice unless the relationship is clearly wrong (pattern 13) or they ask to change it.
- Keep legal, medical, and technical terms exact.
- Don't add deliberate typos, teen code ("rùi", "kô", "mik"), or other tricks aimed at fooling AI detectors. The goal is good Vietnamese, not detector evasion.
- Don't announce "Đây là phiên bản đã được viết lại một cách tự nhiên hơn". That line is itself an AI tell.
