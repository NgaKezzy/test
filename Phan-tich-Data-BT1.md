# BÀI TẬP 1 — PHÂN TÍCH HÀNH VI KHÁCH HÀNG
### Bộ dữ liệu: Global Superstore (`Data.xlsx`, sheet `Orders`)

---

## 0. TỔNG QUAN DỮ LIỆU

| Chỉ tiêu | Giá trị |
|---|---|
| Số dòng giao dịch | 51.290 |
| Số đơn hàng (Order ID) | 25.728 |
| Số khách hàng (Customer ID) | 17.415 |
| Số sản phẩm | 3.788 |
| Phạm vi địa lý | 165 quốc gia, 3.650 thành phố, 5 thị trường |
| Khoảng thời gian | 01/01/2014 – 31/12/2017 (4 năm) |
| Tổng doanh thu | 12.642.502 |
| Tổng lợi nhuận | 1.467.457 (biên 11,6%) |

**Lưu ý phương pháp:** cột `Return` chỉ có giá trị `Yes` (5.752 dòng) và rỗng/`#N/A`. Bài này coi rỗng = *không trả hàng*. Tỷ lệ trả hàng được tính ở **cấp đơn hàng** (đã kiểm tra: cờ trả hàng luôn đồng nhất trong cùng một Order ID — 0/25.728 đơn bị mâu thuẫn).

---

## CÂU 1 — KHÁCH HÀNG TẬP TRUNG Ở ĐÂU?

### 1.1. Theo thị trường (Market)

| Market | Số KH | % KH | Số đơn | Doanh thu | % DT | AOV | Biên LN |
|---|---|---|---|---|---|---|---|
| Asia Pacific | 4.941 | 28,4% | 7.080 | 4.042.658 | **32,0%** | 571 | 10,0% |
| Europe | 4.035 | 23,2% | 6.013 | 3.287.336 | 26,0% | 547 | 13,7% |
| USCA | 2.682 | 15,4% | 5.203 | 2.364.129 | 18,7% | 454 | 12,9% |
| LATAM | 3.702 | 21,3% | 5.144 | 2.164.605 | 17,1% | 421 | 10,2% |
| Africa | 2.055 | 11,8% | 2.288 | 783.773 | 6,2% | 343 | 11,3% |

### 1.2. Theo quốc gia — mức độ tập trung cao

| Hạng | Quốc gia | % Doanh thu | AOV | Biên LN |
|---|---|---|---|---|
| 1 | Hoa Kỳ | **18,2%** | 460 | 12,5% |
| 2 | Úc | 7,3% | 652 | 11,2% |
| 3 | Pháp | 6,8% | 583 | 12,7% |
| 4 | Trung Quốc | 5,5% | 757 | **21,5%** |
| 5 | Đức | 5,0% | 617 | 17,1% |
| 6–10 | Mexico, Ấn Độ, Anh, Indonesia, Brazil | 19,8% | — | — |

> **Top 5 quốc gia = 42,8% doanh thu; Top 10 = 62,6%** trong khi có tới 165 quốc gia.
> Đây là phân bố **"đầu dài – đuôi mỏng"** rất rõ: doanh nghiệp phủ rộng nhưng doanh thu dồn vào một nhóm nhỏ thị trường lõi.

### 1.3. Theo vùng (Region) — 3 vùng dẫn đầu

- **Western Europe** — 13,7% DT (Pháp, Đức, Anh)
- **Central America** — 9,7% DT (Mexico, El Salvador)
- **Oceania** — 8,7% DT, AOV cao thứ nhì (631)

Hai vùng có AOV cao nhất là **Eastern Asia (736)** và **Southern Asia (644)**, đồng thời biên lợi nhuận tốt nhất (19,5% và 18,4%) → đây là vùng "chất lượng cao".

### 1.4. Theo thành phố — phân tán, không có cụm đô thị thống trị

| Thành phố | % DT | Biên LN |
|---|---|---|
| New York City | 2,0% | 24,2% |
| Los Angeles | 1,4% | 17,3% |
| Manila | 1,0% | **–9,2%** |
| Seattle | 0,9% | 24,4% |
| San Francisco | 0,9% | 15,5% |
| Philadelphia | 0,9% | **–12,7%** |

> **Top 10 thành phố chỉ chiếm 10,0% doanh thu, Top 50 chiếm 25,8%.**
> Ngược với cấp quốc gia, ở cấp thành phố khách hàng **rất phân tán**. Hàm ý: marketing nên nhắm theo **quốc gia/vùng**, không nên nhắm theo thành phố (trừ NYC và LA).

### 1.5. Theo phân khúc (Segment)

Consumer 51,6% KH – Corporate 30,0% – Home Office 18,4%. Tỷ trọng doanh thu **gần như trùng khớp** tỷ trọng khách hàng (51,5% / 30,3% / 18,3%) và AOV gần bằng nhau (490–495) → **phân khúc không phải là biến phân hóa hành vi**.

### 1.6. Cảnh báo: vùng tăng trưởng ≠ vùng sinh lời

Các quốc gia **lỗ nặng nhất**: Thổ Nhĩ Kỳ (–98.447, biên –90,7%), Nigeria (–80.751, biên –148,6%), Hà Lan (–41.070), Honduras (–29.482). Southeastern Asia chỉ đạt biên 2,0% dù chiếm 7,0% doanh thu.

**➡️ Kết luận câu 1:** Khách hàng tập trung ở **Asia Pacific và Europe (58% doanh thu)**, với **Hoa Kỳ là thị trường đơn lẻ lớn nhất (18,2%)**. Tập trung cao ở cấp quốc gia nhưng phân tán ở cấp thành phố. Nhóm thị trường "vừa lớn vừa lời" là Trung Quốc, Ấn Độ, Anh, Đức; nhóm cần rà soát giá/chi phí là Thổ Nhĩ Kỳ, Nigeria, Hà Lan.

---

## CÂU 2 — KHÁCH HÀNG THƯỜNG MUA GÌ?

### 2.1. Theo danh mục (Category) — nghịch lý doanh thu vs sản lượng

| Category | % số dòng | % sản lượng | % doanh thu | Giá TB/SP | Biên LN |
|---|---|---|---|---|---|
| Office Supplies | **61,0%** | **60,7%** | 30,0% | 35 | 13,7% |
| Technology | 19,8% | 19,7% | **37,5%** | 135 | **14,0%** |
| Furniture | 19,2% | 19,6% | 32,5% | 118 | **6,9%** |

> **Office Supplies là thứ khách hàng mua *thường xuyên nhất*** (6/10 mặt hàng bán ra) nhưng chỉ tạo 30% doanh thu — đây là nhóm **"kéo khách vào giỏ"**.
> **Technology là thứ tạo *tiền* nhiều nhất** (37,5% DT, biên 14,0%) dù tần suất thấp.
> **Furniture là điểm yếu**: doanh thu lớn thứ nhì nhưng biên chỉ 6,9% — bằng một nửa hai nhóm kia.

### 2.2. Theo phân nhóm (Sub-Category)

**Xếp theo DOANH THU (nhóm tạo tiền):**

| Sub-Category | % DT | Giá TB | Biên LN | Giảm giá TB |
|---|---|---|---|---|
| Phones | 13,5% | 144 | 12,7% | 15% |
| Copiers | 11,9% | 203 | **17,1%** | 12% |
| Chairs | 11,9% | 122 | 9,4% | 16% |
| Bookcases | 11,6% | 176 | 11,0% | 15% |
| Storage | 8,9% | 67 | 9,6% | 14% |
| Appliances | 8,0% | 168 | 14,0% | 14% |
| **Tables** | 6,0% | 246 | **–8,5%** | **29%** |

**Xếp theo TẦN SUẤT (nhóm kéo khách):**

| Sub-Category | Có mặt trong % đơn | % DT | Biên LN |
|---|---|---|---|
| Binders | **21,1%** | 3,7% | 15,7% |
| Storage | 17,7% | 8,9% | 9,6% |
| Art | 17,1% | 2,9% | 15,6% |
| Paper | 12,4% | 1,9% | **24,0%** |
| Chairs | 12,4% | 11,9% | 9,4% |
| Phones | 12,2% | 13,5% | 12,7% |

> **Hai danh sách gần như không giao nhau.** Thứ khách mua *nhiều lần* (Binders, Art, Paper, Labels — giá 8–23/đơn vị) khác hoàn toàn thứ khách *chi nhiều tiền* (Phones, Copiers, Chairs, Bookcases). Chỉ có **Phones, Chairs và Storage** nằm ở cả hai nhóm.

### 2.3. Sản phẩm cụ thể

**Top doanh thu** bị chiếm gần như trọn vẹn bởi 2 dòng sản phẩm:
- **Điện thoại thông minh** (Apple 86.936 · Cisco 76.442 · Motorola 73.156 · Nokia 71.905)
- **Ghế da điều hành** (Hon 58.193 · Office Star 50.662 · Harbour Creations 50.122)
- Ngoại lệ đáng chú ý: *Canon imageCLASS 2200 Copier* — chỉ **5 đơn hàng** nhưng tạo **61.600 doanh thu và 25.200 lợi nhuận** (sản phẩm có LN tuyệt đối cao nhất toàn bộ danh mục).

**Top tần suất** lại là hàng văn phòng phẩm giá rẻ: *Staples* (222 đơn, chỉ 7.008 DT), *Cardinal Index Tab* (92 đơn), *Eldon File Cart* (90 đơn).

**Sản phẩm phá hoại lợi nhuận:** *Cubify CubeX 3D Printer* (–8.880 chỉ với 3 đơn), *Lexmark MX611dhe* (–4.590), *Motorola Smart Phone Cordless* (–4.447).

### 2.4. Cơ cấu giỏ hàng gần như đồng nhất mọi nơi

Tỷ trọng Technology theo thị trường dao động rất hẹp: 36,4% (LATAM) → 41,1% (Africa). Theo phân khúc: 37,1% → 39,0%.
**➡️ Không cần chiến lược sản phẩm riêng theo vùng/phân khúc** — khác biệt thực sự nằm ở *quy mô*, không phải *sở thích*.

**➡️ Kết luận câu 2:** Khách hàng mua **văn phòng phẩm với tần suất cao và giá trị thấp** (Binders, Art, Paper), nhưng doanh thu đến từ **Technology và Furniture giá trị cao mua thưa** (Phones, Copiers, Chairs, Bookcases). Cần bảo vệ Technology (biên tốt nhất) và **xử lý gấp Tables** — nhóm duy nhất lỗ, nguyên nhân là mức giảm giá trung bình 29%, gấp đôi mặt bằng chung.

---

## CÂU 3 — KHÁCH HÀNG CHI BAO NHIÊU MỖI LẦN ĐẶT?

### 3.1. Phân bố giá trị đơn hàng

| Thống kê | Giá trị |
|---|---|
| Trung bình (AOV) | **491,4** |
| **Trung vị** | **201,6** |
| Phân vị 25% | 62,2 |
| Phân vị 75% | 597,8 |
| Phân vị 90% | 1.283,7 |
| Phân vị 99% | 3.725,5 |
| Lớn nhất | 23.661,2 |
| Độ lệch chuẩn | 789,6 |

> **Trung bình (491) gấp 2,4 lần trung vị (202)** → phân phối **lệch phải rất mạnh**. Con số "AOV 491" gây hiểu nhầm: **hơn một nửa số đơn thực tế dưới 202**. Khi viết luận nên dùng **trung vị** làm đại diện.

Quy mô giỏ hàng: trung bình **1,99 dòng/đơn** nhưng **trung vị chỉ 1 dòng** — đa số đơn chỉ mua đúng một sản phẩm. Trung bình 6,9 đơn vị sản phẩm/đơn.

### 3.2. Phân khúc giá trị đơn — quy luật Pareto

| Khoảng giá trị | % số đơn | % doanh thu | Biên LN |
|---|---|---|---|
| < 100 | **34,1%** | 3,0% | **1,8%** |
| 100 – 250 | 20,8% | 7,0% | 4,9% |
| 250 – 500 | 16,2% | 11,8% | 5,8% |
| 500 – 1.000 | 14,9% | 21,6% | 9,9% |
| 1.000 – 2.500 | 11,2% | **34,4%** | 12,5% |
| > 2.500 | 2,9% | 22,3% | **18,4%** |

> **20% đơn hàng lớn nhất tạo 67,0% doanh thu.**
> **Phát hiện quan trọng:** 34% số đơn (giá trị <100) chỉ đóng góp 3% doanh thu với biên lợi nhuận **1,8%** — sau khi trừ chi phí xử lý và vận chuyển, nhóm này gần như chắc chắn **lỗ**. Ngược lại, đơn >2.500 có biên 18,4%, gấp 10 lần.
> Biên lợi nhuận **tăng đơn điệu** theo giá trị đơn → đây là bằng chứng mạnh cho chính sách **giá trị đơn tối thiểu** hoặc **phí xử lý đơn nhỏ**.

### 3.3. Khác biệt theo thị trường

| Market | AOV | Trung vị |
|---|---|---|
| Asia Pacific | 571 | 240 |
| Europe | 547 | 256 |
| USCA | 454 | 150 |
| LATAM | 421 | 194 |
| Africa | 343 | 130 |

USCA đông đơn nhưng giá trị mỗi đơn thấp (trung vị 150); APAC/Europe ít đơn hơn nhưng mỗi đơn lớn hơn ~70%.
Theo phân khúc: Consumer 490 – Corporate 495 – Home Office 490 → **không khác biệt**.

### 3.4. AOV đi ngang suốt 4 năm

2014: 500 → 2015: 489 → 2016: 495 → 2017: 486. Trung vị dao động 199–204.
**➡️ Toàn bộ tăng trưởng của doanh nghiệp đến từ *số lượng đơn*, không phải từ việc khách chi nhiều hơn.** Đây là dư địa chưa khai thác: chỉ cần nâng AOV 10% là có thêm ~1,26 triệu doanh thu mà không cần thêm một khách hàng nào.

**➡️ Kết luận câu 3:** Khách hàng điển hình chi **~202 mỗi lần đặt** (không phải 491), mua **1 sản phẩm**, với ~7 đơn vị. Cấu trúc phân cực: một đuôi dài đơn nhỏ gần như không sinh lời và một nhóm nhỏ đơn lớn gánh toàn bộ lợi nhuận.

---

## CÂU 4 — XU HƯỚNG MUA HÀNG THEO THỜI GIAN

### 4.1. Tăng trưởng theo năm

| Năm | Số đơn | Số KH | Doanh thu | Tăng DT | Tăng đơn | AOV | Biên LN |
|---|---|---|---|---|---|---|---|
| 2014 | 4.515 | 4.163 | 2.259.451 | — | — | 500 | 11,0% |
| 2015 | 5.473 | 4.946 | 2.677.439 | +18,5% | +21,2% | 489 | 11,5% |
| 2016 | 6.883 | 6.111 | 3.405.746 | +27,2% | +25,8% | 495 | 12,0% |
| 2017 | 8.857 | 7.621 | 4.299.866 | +26,3% | +28,7% | 485 | 11,7% |

> **CAGR doanh thu 23,9%/năm; CAGR số đơn 25,2%/năm.**
> Số đơn tăng **nhanh hơn** doanh thu → AOV giảm nhẹ. Doanh nghiệp đang **tăng trưởng theo chiều rộng** (thêm khách, thêm đơn) chứ không theo chiều sâu.
> Biên lợi nhuận **ổn định 11–12%** qua cả 4 năm → tăng trưởng không đánh đổi bằng lợi nhuận. Đây là tín hiệu lành mạnh.

### 4.2. Tính mùa vụ rất rõ rệt

| Tháng | Chỉ số mùa vụ | Tháng | Chỉ số mùa vụ |
|---|---|---|---|
| 1 | 0,64 | 7 | 0,71 |
| **2** | **0,53** ⬇️ thấp nhất | 8 | 1,23 |
| 3 | 0,72 | **9** | **1,36** |
| 4 | 0,66 | 10 | 1,12 |
| 5 | 0,87 | **11** | **1,47** |
| 6 | 1,20 | **12** | **1,49** ⬆️ cao nhất |

*(Chỉ số 1,00 = mức trung bình tháng. Tháng 12 bán gấp **2,8 lần** tháng 2.)*

**Quy luật:**
- **Nửa cuối năm (T8–T12) chiếm 55,6% doanh thu cả năm**; riêng Q4 là 8.613 đơn — quý lớn nhất mọi năm.
- Có **3 đỉnh**: tháng 6 (1,20), tháng 8–9 (1,23–1,36 — mùa tựu trường/khai giảng, hợp với danh mục văn phòng phẩm), và tháng 11–12 (1,47–1,49 — mùa lễ + chốt ngân sách năm).
- **Hai đáy**: tháng 1–2 và tháng 4, tháng 7.
- Tháng cao nhất toàn kỳ: **11/2017 (555.279)**; thấp nhất: **02/2015 (98.855)** — chênh 5,6 lần.

### 4.3. Tăng trưởng không đồng đều giữa các thị trường

| Market | 2014 | 2017 | Tăng trưởng 2014→2017 |
|---|---|---|---|
| Africa | 127.187 | 283.036 | **+123%** |
| Europe | 540.751 | 1.180.304 | **+118%** |
| Asia Pacific | 713.658 | 1.372.784 | +92% |
| LATAM | 385.098 | 706.633 | +83% |
| USCA | 492.757 | 757.108 | **+54%** |

> **Europe là động lực tăng trưởng thực sự**: vừa quy mô lớn (26% DT) vừa tăng +118%.
> **USCA đang chững lại** — tăng chậm nhất (+54%), thậm chí *giảm* nhẹ trong 2015 (486.629 so với 492.757 của 2014). Thị trường lớn nhất đang bão hòa.
> Africa tăng nhanh nhất nhưng nền quá thấp (6,2% DT).

### 4.4. Chu kỳ trong tháng

Doanh thu phân bổ khá đều giữa đầu tháng (4,01tr), giữa tháng (4,34tr) và cuối tháng (4,29tr) → **không có hiệu ứng "chốt đơn cuối tháng"**.

*(Ghi chú: dữ liệu cho thấy thứ Tư và thứ Năm có lượng đơn rất thấp (6,1% và 8,5%) so với các ngày khác (~17–18%). Đây nhiều khả năng là đặc thù cách sinh dữ liệu của bộ Global Superstore chứ không phải hành vi thật, nên không nên rút kết luận kinh doanh từ chiều này.)*

**➡️ Kết luận câu 4:** Doanh nghiệp tăng trưởng mạnh và ổn định (**CAGR 23,9%**), nhưng hoàn toàn nhờ **mở rộng số lượng đơn**. Hoạt động kinh doanh có **tính mùa vụ mạnh**, dồn vào Q4 và mùa tựu trường; tháng 1–2 và tháng 4, 7 là mùa thấp điểm → nên dồn tồn kho/nhân sự/ngân sách quảng cáo vào T8–T12 và dùng T1–T4 để chạy chương trình kích cầu.

---

## CÂU 5 — DẤU HIỆU KHÁCH HÀNG CÓ NGUY CƠ TRẢ HÀNG ⭐

*(Đây là câu được chọn trong nhóm câu 5–8 "Chọn 1 trong 4")*

### 5.1. Quy mô vấn đề

| Chỉ tiêu | Giá trị |
|---|---|
| Đơn bị trả | 1.970 / 25.728 = **7,66%** |
| Dòng hàng bị trả | 5.752 / 51.290 = 11,21% |
| Doanh thu bị trả | 1.357.443 / 12.642.502 = **10,74%** |
| Lợi nhuận bị cuốn theo | **136.597** (≈ 9,3% tổng lợi nhuận) |

> Doanh thu bị trả (10,7%) **cao hơn** tỷ lệ đơn bị trả (7,7%) → **đơn bị trả có giá trị lớn hơn đơn bình thường**. Đây là manh mối đầu tiên.

Toàn bộ phân tích dưới đây dùng **Lift** = tỷ lệ trả của nhóm ÷ 7,66% (mức nền). Lift > 1 = rủi ro cao hơn bình thường.

---

### 5.2. ⭐ DẤU HIỆU MẠNH NHẤT: SỐ DÒNG HÀNG TRONG ĐƠN

| Số dòng/đơn | Số đơn | Tỷ lệ trả | Lift |
|---|---|---|---|
| 1 | 12.935 | **3,94%** | 0,51× |
| 2 | 6.382 | 8,01% | 1,05× |
| 3 | 3.238 | 11,61% | 1,52× |
| 4–5 | 2.368 | 15,50% | 2,02× |
| **6+** | 805 | **25,71%** | **3,36×** |

> **Chênh lệch 6,5 lần** giữa đơn 1 dòng và đơn 6+ dòng. Đây là biến dự báo mạnh nhất trong toàn bộ dữ liệu (tương quan 0,189).
> Cứ **4 đơn có từ 6 dòng trở lên thì 1 đơn bị trả**.

### 5.3. ⭐ ĐỘ ĐA DẠNG CỦA GIỎ HÀNG

| Số phân nhóm SP khác nhau | Số đơn | Tỷ lệ trả | Lift |
|---|---|---|---|
| 1 | 13.491 | 4,09% | 0,53× |
| 2 | 6.611 | 8,46% | 1,10× |
| 3 | 3.208 | 12,75% | 1,67× |
| **4+** | 2.418 | **18,61%** | **2,43×** |

Giỏ càng trộn nhiều loại hàng, rủi ro càng cao — phù hợp với giả thuyết **"mua thăm dò/mua gộp rồi chọn lại"**.

### 5.4. ⭐ SỐ LƯỢNG SẢN PHẨM

| Số lượng/đơn | Số đơn | Tỷ lệ trả | Lift |
|---|---|---|---|
| 1–2 | 5.929 | 4,32% | 0,56× |
| 3–5 | 7.673 | 5,36% | 0,70× |
| 6–10 | 6.945 | 8,19% | 1,07× |
| 11–20 | 4.197 | 12,72% | 1,66× |
| **>20** | 984 | **20,33%** | **2,65×** |

### 5.5. ⚠️ GIÁ TRỊ ĐƠN HÀNG — TƯƠNG QUAN GIẢ (phát hiện quan trọng)

Nhìn thô, giá trị đơn có vẻ là dấu hiệu rõ ràng:

| Giá trị đơn | Tỷ lệ trả | Lift |
|---|---|---|
| <100 | 4,84% | 0,63× |
| 100–250 | 6,77% | 0,88× |
| 250–500 | 9,26% | 1,21× |
| 500–1.000 | 9,66% | 1,26× |
| 1.000–2.500 | 11,29% | 1,47× |
| >2.500 | 13,87% | 1,81× |

**Nhưng khi kiểm soát số dòng hàng, hiệu ứng này gần như biến mất:**

| Số dòng | Giá trị đơn | Số đơn | Tỷ lệ trả |
|---|---|---|---|
| 1 dòng | <250 | 9.711 | 3,88% |
| 1 dòng | 250–1k | 2.561 | 4,18% |
| 1 dòng | **>1k** | 663 | **3,77%** ← không hề cao hơn |
| 2 dòng | <250 | 3.187 | 8,16% |
| 2 dòng | **>1k** | 798 | **6,27%** ← thậm chí *thấp hơn* |
| 3+ dòng | <250 | 1.226 | 12,23% |
| 3+ dòng | >1k | 2.167 | 16,34% |

> **Kết luận phương pháp:** Đơn đắt tiền *không* rủi ro hơn vì nó đắt — mà vì đơn đắt thường có nhiều món hơn. **Nguyên nhân thật là quy mô giỏ hàng, không phải giá trị tiền.**
> Đây là ví dụ điển hình về sai lầm "tương quan ≠ nhân quả" cần nêu trong bài luận: nếu chỉ nhìn bảng đầu, doanh nghiệp sẽ đi siết đơn giá trị cao — một quyết định sai và gây thiệt hại doanh thu.

### 5.6. GIẢM GIÁ — có tác động nhưng yếu và có điều kiện

| Giảm giá cao nhất trong đơn | Tỷ lệ trả | Lift |
|---|---|---|
| 0% | 6,78% | 0,89× |
| 0–10% | 7,83% | 1,02× |
| 10–20% | 7,98% | 1,04× |
| 20–40% | 8,88% | 1,16× |
| **>40%** | **9,43%** | **1,23×** |

Kiểm soát theo số dòng cho thấy **giảm giá chỉ thực sự có hại ở đơn lớn**:

| Số dòng | Giảm giá 0% | Giảm giá >20% | Chênh lệch |
|---|---|---|---|
| 1 dòng | 3,69% | 4,29% | +0,6 điểm |
| 2 dòng | 7,84% | 8,66% | +0,8 điểm |
| **3+ dòng** | 13,88% | **16,62%** | **+2,7 điểm** |

→ Khuyến mãi sâu áp lên **giỏ hàng lớn** là tổ hợp nguy hiểm nhất.

### 5.7. GIAO HÀNG SIÊU TỐC — rủi ro với đơn nhỏ

| Ship Mode | Tỷ lệ trả | Lift |
|---|---|---|
| **Same Day** | **8,82%** | 1,15× |
| First Class | 7,66% | 1,00× |
| Standard Class | 7,59% | 0,99× |
| Second Class | 7,56% | 0,99× |

Sau khi kiểm soát quy mô đơn, hiệu ứng chỉ tồn tại ở **đơn nhỏ**: đơn 1 dòng Same Day trả **5,03%** so với 3,87% ở phương thức khác (+30%); đơn 2 dòng: 10,53% vs 7,86% (+34%); đơn 3+ dòng: không chênh lệch.
→ Dấu hiệu của **mua bốc đồng** (impulse buy): cần gấp, giao ngay, rồi đổi ý.

### 5.8. ĐỊA LÝ — rủi ro theo vùng

**Quốc gia rủi ro cao nhất (≥150 đơn):** Philippines 11,35% (1,48×) · Colombia 10,43% · Morocco 10,00% · New Zealand 9,84% · Ukraine 9,72% · Thổ Nhĩ Kỳ 9,28%
**Quốc gia an toàn nhất:** Iran 5,30% · Ai Cập 5,31% · Panama 5,53% · Canada 5,85%

**Thành phố rủi ro cao nhất (≥80 đơn):** Perth 13,98% · Madrid 13,79% · Manila 12,14% · Seattle 11,37% · Canberra 11,25% · Chicago 10,53%
**Thành phố an toàn nhất:** Panama City 3,57% · Brisbane 4,08% · Sydney 4,58% · Cairo 4,72%

**Vùng:** Eastern Africa 10,08% (1,32×) và Southeastern Asia 8,97% (1,17×) cao nhất; Central Asia thấp bất thường 0,89% (chỉ 112 đơn — mẫu nhỏ, cần thận trọng).

> ⚠️ Lưu ý: **Manila** (12,14% trả hàng) đồng thời là thành phố có biên lợi nhuận **–9,2%**. Trả hàng và thua lỗ đang xảy ra ở cùng một nơi.

### 5.9. THỜI ĐIỂM

Tháng 10 (8,69%), tháng 1 (8,61%), tháng 8 (8,17%) cao nhất; tháng 2 (6,72%) và tháng 6 (6,78%) thấp nhất. Theo quý: Q4 8,13% > Q1 7,82% > Q3 7,62% > Q2 6,93%.
→ **Mùa cao điểm (Q4) cũng là mùa trả hàng cao điểm**, và tháng 1 là "đuôi" trả hàng sau lễ.

### 5.10. LỢI NHUẬN ĐƠN HÀNG

| Lợi nhuận đơn | Tỷ lệ trả | Lift |
|---|---|---|
| **Lỗ** | **9,01%** | 1,18× |
| 0–50 | 5,25% | 0,69× |
| 50–200 | 8,65% | 1,13× |
| >200 | 11,26% | 1,47× |

Đơn đang lỗ có rủi ro trả hàng cao hơn 18% so với mức nền — **lỗ chồng lỗ**.

### 5.11. ❌ NHỮNG DẤU HIỆU KHÔNG CÓ TÁC DỤNG (cũng quan trọng để nêu)

| Biến | Kết quả | Nhận định |
|---|---|---|
| **Phân khúc KH** | Corporate 7,74% · Consumer 7,62% · Home Office 7,62% | **Không phân biệt** |
| **Danh mục SP** | Office Supplies 11,29% · Furniture 11,18% · Technology 11,02% | **Không phân biệt** |
| **Phân nhóm SP** | Fasteners 12,15% cao nhất → Labels 10,30% thấp nhất | Chênh lệch chỉ ±8%, **không đáng kể** |
| **Mức độ ưu tiên đơn** | Critical 7,81% → Low 7,24% | **Không phân biệt** |
| **Tần suất mua của KH** | KH mua 1 đơn 7,77% · KH mua 6+ đơn 7,27% | **Không phân biệt** |
| **Lịch sử trả hàng** | KH từng trả: 7,98% vs chưa từng trả: 7,41% (chỉ 1,08×) | **Rất yếu** |
| **Thời gian giao hàng** | 0 ngày 8,67% → 7+ ngày 6,63% | Ngược chiều trực giác, yếu |

> **Phát hiện phản trực giác đáng nêu trong bài luận:** thông thường "khách từng trả hàng sẽ trả hàng tiếp" là quy luật vàng của ngành bán lẻ. Ở bộ dữ liệu này **điều đó không đúng**: chỉ 69 khách hàng (0,4%) trả hàng từ 2 lần trở lên, và việc đã từng trả hàng chỉ làm tăng rủi ro **1,08 lần** — không đủ để làm cơ sở ra quyết định.
> **Hàm ý:** rủi ro trả hàng ở đây gắn với **đặc điểm của đơn hàng**, không gắn với **con người**. Vì vậy giải pháp phải nhắm vào *khâu đặt hàng*, không nhắm vào *danh sách khách hàng đen*.

### 5.12. Bảng xếp hạng sức mạnh dự báo (tương quan point-biserial)

| Hạng | Biến | Hệ số |
|---|---|---|
| 1 | Số dòng hàng/đơn | **0,189** |
| 2 | Số phân nhóm khác nhau | 0,183 |
| 3 | Tổng số lượng SP | 0,153 |
| 4 | Giá trị đơn | 0,072 |
| 5 | Mức giảm giá cao nhất | 0,038 |

### 5.13. Chân dung đơn hàng rủi ro cao

> **"Giỏ hàng lớn, trộn nhiều loại (≥4 dòng, ≥3 phân nhóm, ≥11 đơn vị), có món giảm giá trên 20%, đặt vào Q4 hoặc tháng 1, giao tới Philippines / Manila / Perth / Madrid / Seattle."**
> Nhóm này có tỷ lệ trả hàng **15–26%**, tức gấp **2–3,4 lần** mức bình thường.
>
> Ngược lại, **đơn 1 dòng, không giảm giá, giao Standard Class** chỉ trả **3,69%** — an toàn gấp đôi mức trung bình.

### 5.14. Khuyến nghị hành động

1. **Chấm điểm rủi ro tại giỏ hàng** — dùng 3 biến số dòng / số phân nhóm / số lượng (không cần mô hình phức tạp, đã giải thích được phần lớn biến thiên). Đơn đạt ngưỡng rủi ro cao → kích hoạt xác nhận bổ sung trước khi giao.
2. **Cải thiện trang sản phẩm cho giỏ hàng lớn** — rủi ro tăng theo *độ đa dạng* cho thấy khách không chắc chắn về thứ mình chọn: bổ sung bảng thông số, ảnh thật, kích thước, đánh giá.
3. **Giới hạn khuyến mãi sâu trên giỏ lớn** — giảm giá >20% kết hợp giỏ 3+ dòng làm tăng 2,7 điểm phần trăm; nên chặn tổ hợp này bằng quy tắc khuyến mãi.
4. **Rà soát Same Day cho đơn nhỏ** — thêm một bước xác nhận hoặc kéo dài cửa sổ hủy đơn (chi phí thấp, tác động trực tiếp lên hành vi bốc đồng).
5. **Can thiệp theo địa bàn, không theo khách hàng** — vì rủi ro gắn với đơn chứ không gắn với người, nên ưu tiên xử lý 6 thị trường rủi ro cao (Philippines, Colombia, Morocco, New Zealand, Ukraine, Turkey) về mặt mô tả sản phẩm, đóng gói và đối tác giao vận.
6. **Chuẩn bị nguồn lực xử lý hoàn trả cho Q4 và tháng 1** — đây là đỉnh kép của cả doanh thu lẫn trả hàng.

---

## CÂU 9 — BAO LÂU KHÁCH HÀNG QUAY TRỞ LẠI?

### 9.1. Phần lớn khách hàng không quay lại

| Số đơn/KH | Số KH | % |
|---|---|---|
| **1 đơn** | 11.981 | **68,8%** |
| 2 đơn | 3.466 | 19,9% |
| 3 đơn | 1.313 | 7,5% |
| 4 đơn | 454 | 2,6% |
| 5 đơn | 157 | 0,9% |
| 6+ đơn | 42 | 0,2% |

> **Gần 7/10 khách hàng chỉ mua đúng một lần trong suốt 4 năm.** Chỉ 31,2% quay lại từ lần thứ hai.
> Đây là vấn đề nghiêm trọng nhất lộ ra từ toàn bộ dữ liệu.

### 9.2. Khoảng cách giữa hai lần mua

| Thống kê | Giá trị |
|---|---|
| Số lần quan sát | 8.314 |
| **Trung vị** | **303 ngày (~10 tháng)** |
| Trung bình | 379 ngày |
| Phân vị 10% | 46 ngày |
| Phân vị 25% | 127 ngày |
| Phân vị 75% | 563 ngày |
| Phân vị 90% | 833 ngày |

| Khoảng cách | Tỷ lệ | Lũy kế |
|---|---|---|
| ≤ 1 tháng | 6,5% | 6,5% |
| 1–3 tháng | 12,1% | 18,6% |
| 3–6 tháng | 14,6% | 33,3% |
| 6–12 tháng | 24,1% | **57,4%** |
| 1–2 năm | 27,7% | 85,1% |
| > 2 năm | 14,9% | 100% |

> **Chu kỳ mua lại điển hình là ~10 tháng** — rất dài. Chỉ 18,6% khách quay lại trong vòng 3 tháng, trong khi 42,6% mất hơn một năm.

### 9.3. Tỷ lệ mua lại theo cửa sổ thời gian

*(Chỉ tính 12.778 khách hàng có đủ tối thiểu 365 ngày theo dõi — tránh sai lệch do khách mới mua cuối kỳ)*

| Cửa sổ | Tỷ lệ mua lại |
|---|---|
| 30 ngày | 1,5% |
| 60 ngày | 3,1% |
| 90 ngày | 4,6% |
| 180 ngày | 9,0% |
| **365 ngày** | **17,7%** |

> Sau **một năm trọn vẹn**, chưa tới 1/5 khách hàng quay lại. Cửa sổ 30 ngày gần như bằng không (1,5%) → **không có hành vi mua lặp ngắn hạn**, kể cả với danh mục văn phòng phẩm tiêu hao vốn lẽ ra phải mua định kỳ. Đây là dấu hiệu doanh nghiệp **chưa chiếm được đơn hàng bổ sung định kỳ** của khách.

### 9.4. ⭐ Chu kỳ rút ngắn dần theo số lần mua

| Lần mua thứ | Số quan sát | Khoảng cách trung vị | Trung bình |
|---|---|---|---|
| 1 → 2 | 5.433 | **364 ngày** | 432 |
| 2 → 3 | 1.967 | **250 ngày** | 309 |
| 3 → 4 | 654 | **168 ngày** | 228 |
| 4 → 5 | 200 | **133 ngày** | 189 |
| 5 → 6 | 43 | 149 ngày | 172 |

> **Phát hiện quan trọng nhất của câu này:** mỗi lần khách quay lại, khoảng cách tới lần sau **rút ngắn khoảng 30%**. Từ 364 ngày (lần 2) xuống còn 133 ngày (lần 5) — **nhanh hơn 2,7 lần**.
> **Hàm ý chiến lược:** rào cản lớn nhất nằm ở **đơn hàng thứ hai**. Nếu đưa được khách qua mốc đó, hành vi mua sẽ tự tăng tốc. Ngân sách giữ chân nên dồn gần như toàn bộ vào cửa sổ **0–12 tháng sau đơn đầu tiên**, không rải đều cho mọi khách hàng.

### 9.5. Khách quay lại có giá trị gấp 2,75 lần

| Nhóm | Số KH | % KH | % Doanh thu | Giá trị TB/KH | Số đơn TB |
|---|---|---|---|---|---|
| Mua 1 lần | 11.981 | 68,8% | 44,5% | 469 | 1,0 |
| **Quay lại** | 5.433 | **31,2%** | **55,5%** | **1.292** | 2,5 |

> **31,2% khách hàng tạo ra 55,5% doanh thu.** Mỗi khách quay lại đáng giá 1.292 so với 469 của khách một lần.
> Ước tính tác động: nếu nâng tỷ lệ quay lại từ 31,2% lên 40% (thêm ~1.530 khách), doanh thu tăng thêm khoảng **1,26 triệu** — tương đương 10% tổng doanh thu 4 năm.

### 9.6. Chênh lệch cực lớn giữa các thị trường

| Market | Số KH | % quay lại | Giá trị TB/KH |
|---|---|---|---|
| **USCA** | 2.681 | **55,1%** | 882 |
| Europe | 4.035 | 31,9% | 815 |
| Asia Pacific | 4.941 | 29,3% | 818 |
| LATAM | 3.702 | 27,3% | 585 |
| **Africa** | 2.055 | **10,2%** | 381 |

> **USCA giữ chân khách gấp 5,4 lần Africa.** Điều này giải thích nghịch lý ở câu 1 và câu 4: USCA có AOV thấp nhất (454) và tăng trưởng chậm nhất (+54%), nhưng lại là thị trường **trưởng thành** — doanh thu đến từ tập khách hàng trung thành đã có, không phải từ việc liên tục săn khách mới.
> Ngược lại, tăng trưởng +123% của Africa được xây trên nền khách hàng gần như **không quay lại** (10,2%) — tăng trưởng này **không bền vững** nếu chi phí thu hút khách mới tăng lên.

Theo phân khúc: Consumer 31,5% · Home Office 31,4% · Corporate 30,6% → **không khác biệt**, tiếp tục khẳng định Segment không phải biến hữu ích trong bộ dữ liệu này.

### 9.7. Khuyến nghị

1. **Chiến dịch "đơn hàng thứ hai"** — tập trung toàn bộ vào 0–6 tháng sau đơn đầu, vì đây là nút thắt duy nhất có đòn bẩy cao (qua được mốc này, chu kỳ tự rút ngắn 30% mỗi lần).
2. **Thiết lập cảnh báo ngủ đông ở mốc 127 ngày** (phân vị 25% của khoảng cách mua lại) — khách vượt mốc này mà chưa quay lại là đang lệch khỏi quỹ đạo bình thường.
3. **Khai thác danh mục tiêu hao để tạo nhịp mua định kỳ** — Binders, Paper, Art, Labels xuất hiện trong 9–21% số đơn nhưng tỷ lệ mua lại 30 ngày chỉ 1,5%. Đăng ký định kỳ hoặc nhắc bổ sung hàng là đòn bẩy trực tiếp.
4. **Nhân rộng mô hình vận hành của USCA sang Europe và APAC** — hai thị trường này có giá trị khách hàng tương đương USCA (815–818 so với 882) nhưng tỷ lệ quay lại chỉ bằng một nửa. Dư địa ở đây lớn hơn ở Africa.

---

## TỔNG KẾT — 6 PHÁT HIỆN CỐT LÕI

| # | Phát hiện | Bằng chứng |
|---|---|---|
| 1 | Doanh thu tập trung ở cấp **quốc gia** nhưng phân tán ở cấp **thành phố** | Top 10 QG = 62,6% DT nhưng Top 10 TP chỉ = 10,0% DT |
| 2 | Thứ khách **mua nhiều** ≠ thứ mang lại **tiền** | Office Supplies 60,7% sản lượng / 30,0% DT; Technology 19,7% sản lượng / 37,5% DT |
| 3 | AOV trung bình **gây hiểu nhầm**; 34% đơn hàng gần như không sinh lời | Trung bình 491 vs trung vị 202; đơn <100 có biên LN 1,8% |
| 4 | Tăng trưởng 23,9%/năm **hoàn toàn nhờ số lượng đơn**, không nhờ giá trị đơn | AOV đi ngang 500→486 suốt 4 năm |
| 5 | Rủi ro trả hàng gắn với **đơn hàng**, không gắn với **khách hàng** | Số dòng/đơn: lift 3,36× — trong khi lịch sử trả hàng của KH chỉ 1,08× |
| 6 | Nút thắt lớn nhất là **đơn hàng thứ hai** | 68,8% KH mua 1 lần; nhưng chu kỳ rút từ 364 → 133 ngày sau mỗi lần quay lại |

---

## GIỚI HẠN CỦA PHÂN TÍCH

- Cột `Return` chỉ ghi nhận `Yes`/rỗng, **không có ngày trả hàng, lý do trả hàng, hay sản phẩm cụ thể bị trả** → không thể phân tích độ trễ hoàn trả hay nguyên nhân.
- Cột `Postal Code` thiếu 41.296/51.290 giá trị (80,5%) → không dùng được cho phân tích vi mô địa lý.
- Không có dữ liệu chi phí marketing, lượt truy cập, hay kênh bán → không tính được CAC hay hiệu quả kênh.
- Phân phối đơn theo thứ trong tuần bất thường (thứ Tư 6,1%) gợi ý dữ liệu có yếu tố mô phỏng → tránh kết luận từ chiều này.
- Các nhóm mẫu nhỏ (Central Asia 112 đơn, khách hàng trả 3+ lần: 2 người) chỉ mang tính tham khảo.
