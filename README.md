# AIDLC cho Android Development: Từ Ticket đến Pull Request với AI Agents

## Giới thiệu

Trong vài năm gần đây, AI đã thay đổi cách chúng ta phát triển phần mềm. Tuy nhiên, phần lớn developer vẫn đang sử dụng AI theo mô hình khá đơn giản:

```
Requirement
    ↓
Prompt AI
    ↓
Code
```

### Vấn đề với cách tiếp cận hiện tại

Cách tiếp cận này có thể giúp tạo code nhanh hơn, nhưng thường dẫn đến nhiều vấn đề:

- Thiếu phân tích requirement
- Bỏ sót edge cases
- Solution không phù hợp với kiến trúc hiện tại
- Tăng số lượng bug
- Khó maintain về lâu dài

### Giải pháp: AIDLC

Để giải quyết bài toán đó, team chúng tôi xây dựng một workflow phát triển tính năng mới dựa trên tư duy AIDLC (**AI-Driven Development Lifecycle**).

**Mục tiêu quan trọng:** Không phải là để AI thay thế Developer, mà là để AI tham gia vào từng giai đoạn của vòng đời phát triển phần mềm.

---

## Tại sao cần AIDLC?

Trong một feature thông thường, thời gian coding thực tế chỉ chiếm một phần nhỏ.

Developer thường phải dành thời gian cho:

- Hiểu requirement
- Phân tích impact
- Đọc code hiện tại
- Thiết kế solution
- Implement
- Viết test
- Review
- Chuẩn bị Pull Request

Nếu AI chỉ tham gia ở bước coding thì chúng ta mới khai thác được một phần rất nhỏ giá trị của nó.

**AIDLC mở rộng vai trò của AI sang toàn bộ vòng đời phát triển feature.**

---

## Workflow tổng thể

```
BA Analyze
    ↓
Context Collector
    ↓
Solution Design
    ↓
Figma Inspect
    ↓
Planning
    ↓
Android Development
    ↓
Unit Test
    ↓
Code Review
    ↓
Dev Check
```

Mỗi bước được đảm nhiệm bởi một AI Agent chuyên biệt với nhiệm vụ và đầu ra rõ ràng.

> **Quan trọng:** Mỗi bước hãy cố gắng nạp đủ các context, kỹ năng, rule, mindset gần nhất với dự án đang apply (cái này sẽ flex cho từng dự án)

---

## Chi tiết từng Agent

### 1. BA Analyze Agent

Agent đầu tiên đóng vai trò **Business Analyst**.

**Input:**
- Jira Ticket
- User Story
- Business Requirement
- BRD

**Output:**
- `BA-SPEC.md`

Agent này giúp chuyển đổi ngôn ngữ business thành ngôn ngữ kỹ thuật.

**Ví dụ:**

Thay vì:
- "User cần xem lịch sử giao dịch"

Agent sẽ phân tích thành:
- Functional Requirements
- Acceptance Criteria
- Error Cases
- Edge Cases
- Business Rules

Kết quả là team có một tài liệu kỹ thuật rõ ràng trước khi bắt đầu thiết kế.

### 2. Context Collector Agent

Đây là agent **quan trọng nhất** nhưng thường bị bỏ qua.

Trước khi thiết kế solution, agent sẽ quét toàn bộ codebase để trả lời các câu hỏi:

- Feature tương tự đã tồn tại chưa?
- API nào đang được sử dụng?
- Repository nào có thể tái sử dụng?
- Navigation hiện tại hoạt động ra sao?
- Design System hiện tại gồm những component nào?

**Output:**
- `CONTEXT-REPORT.md`

Mục tiêu là tránh việc AI tạo ra một solution hoàn toàn mới trong khi dự án đã có sẵn implementation tương tự.

Đây là bước giúp AI hiểu được **"ngữ cảnh của hệ thống"**.

### 3. Solution Design Agent

Sau khi có requirement và context, agent tiếp theo đóng vai trò **Android Architect**.

**Output:**
- `SOLUTION-DESIGN.md`

Agent sẽ xác định:
- Architecture
- Data Flow
- API Contract
- Database Impact
- Module Impact
- Dependency Injection
- Error Handling Strategy

**Nguyên tắc của team:**
> **Không code khi chưa có Solution Design.**

Điều này giúp giảm đáng kể số lần refactor và rework.

### 4. Figma Inspect Agent

Đối với feature có giao diện mới, AI sẽ đọc trực tiếp từ Figma.

**Output:**
- `FIGMA-SPEC.md`

Thông tin được trích xuất:
- Component Hierarchy
- Typography
- Spacing
- Colors
- Design Tokens
- Layout Structure

Developer không còn phải inspect thủ công từng pixel trên Figma.

### 5. Planning Agent

Khi solution đã hoàn thiện, AI bắt đầu lập kế hoạch implementation.

**Output:**
- `IMPLEMENT-PLAN.md`

**Ví dụ:**
- Task 1: API Layer
- Task 2: Repository
- Task 3: Use Case
- Task 4: ViewModel
- Task 5: UI
- Task 6: Navigation
- Task 7: Analytics
- Task 8: Testing

Việc chia nhỏ task giúp AI và Developer làm việc theo từng bước rõ ràng hơn.

### 6. Android Development Agent

Đây là agent được sử dụng nhiều nhất.

**Input:**
- Solution Design
- Figma Spec
- Implementation Plan

Agent implement feature theo các convention của dự án:
- Clean Architecture
- MVVM
- Koin
- Coroutines
- Flow
- Repository Pattern

**Điểm khác biệt:** AI không code từ requirement nữa. AI code từ một **thiết kế đã được chuẩn hóa**.

### 7. Unit Test Agent

Sau khi feature hoàn thành, AI tự động tạo test cases.

**Output:**
- `UNIT-TEST-REPORT.md`

Bao gồm:
- ViewModel Test
- Use Case Test
- Repository Test
- Edge Case Test

Điều này giúp tăng coverage mà không tạo thêm nhiều effort cho Developer.

### 8. Code Review Agent

Agent tiếp theo đóng vai trò **Principal Engineer**.

**Output:**
- `CODE-REVIEW.md`

Các tiêu chí review:
- Architecture
- SOLID Principles
- Naming Convention
- Performance
- Coroutine Usage
- Error Handling
- Maintainability

Review được thực hiện **trước khi** Developer tạo Pull Request.

### 9. Dev Check Agent

Đây là bước cuối cùng trước khi tạo PR.

**Output:**
- `DEV-CHECK.md`

Checklist bao gồm:
- Koin Registration
- Coroutine Safety
- Room Migration
- Analytics Events
- Logging
- Build Variant Compatibility
- Production Readiness

Mục tiêu là giảm các lỗi thường gặp trong quá trình review hoặc release.

---

## Workflow áp dụng thực tế

### New Feature

```
BA Analyze
→ Context Collector
→ Solution Design
→ Figma Inspect
→ Planning
→ Android Development
→ Unit Test
→ Code Review
→ Dev Check
```

### UI Development

```
Figma Inspect
→ Planning
→ Android Development
→ Unit Test
→ Code Review
→ Dev Check
```

---

## Kết quả kỳ vọng

Sau khi áp dụng AIDLC, mục tiêu của team **không phải** là viết code nhanh hơn.

Mục tiêu thực sự là:
- Hiểu requirement tốt hơn
- Thiết kế solution nhất quán hơn
- Tận dụng code hiện có tốt hơn
- Giảm bug production
- Tăng tốc độ review
- Chuẩn hóa chất lượng feature

---

## Kết luận

**AI không thay thế Developer.**

AI trở thành một **thành viên trong team**, tham gia xuyên suốt từ:

```
Requirement → Design → Development → Testing → Review → Release Readiness
```

Đó là cách chúng tôi tiếp cận **AI-Driven Development Lifecycle cho Android Development**.
