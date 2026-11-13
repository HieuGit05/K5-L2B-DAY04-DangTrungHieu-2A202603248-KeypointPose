# Báo cáo cá nhân - Đặng Trung Hiếu - 2A202603248


Dữ liệu: 12 ảnh người COCO val2017 (Lin et al., 2014) và 8 ảnh chân dung Wikimedia Commons, chỉ dùng trong lớp.

## 0. Thông tin học viên

- Họ tên: Đặng Trung Hiếu
- MSSV: 2A202603248
- Email: ladykiller12.2005@gmail.com
- Link repository: https://github.com/HieuGit05/K5-L2B-DAY04-DangTrungHieu-2A202603248-KeypointPose
- Phiên bản CVAT (Help → About):
- Máy: hệ điều hành Win 11 · RAM 16 GB · chạy CVAT chế độ đầy đủ 
- Bộ ảnh (`src/exports/assignment.json` do `lab.py setup` tạo): có 
- Giờ bắt đầu: 16h30 12/11/2026
- Giờ kết thúc: 12h 13/11/2026

## 1. Kiểm tra label (CP0)

| Label | Kiểu | Số điểm | Tên điểm đúng bảng của lab? | Đúng thứ tự? | Số cạnh |
|---|---|---:|---|---|---:|
| `person` | skeleton | 17 | Có | Có | 19 |
| `face` | skeleton | 13 | Có | Có | 13 |

Mẫu `person` dựng theo người quay mặt về camera (các điểm `left_*` nằm bên phải khung mẫu)? Có

Cách đổi cờ `occluded` / `outside` cho **một điểm** trên phiên bản CVAT này (một câu):

Bấm chuột phải vào điểm đó trên ảnh rồi chọn Occluded (hoặc Outside) trong menu hiện ra.

## 2. Số lượng đã gán và thời gian (CP1, CP2)

| Nhóm ảnh | Số ảnh | Số skeleton đã gán | Số người dưới 60 px (không gán) | Số poster / gương / màn hình bỏ qua | Thời gian (phút) |
|---|---:|---:|---:|---:|---:|
| `easy` | 5 |5 | 0 |0 | 30p |
| `occluded` | 3 | 3 |0 |0 |30p |
| `back` | 2 |2 | 0| 0|30p |
| `small` | 1 |1 |0 |0 | 30p|
| `crowd` | 1 | 1| 0| 0| 15p |
| `faces` | 8 |8 | — | 0 | 15p |

- Số ảnh người đã xong ở mốc phút 105: 10 / 10
- Thời gian thực tế (phút): CP1 2h · CP2 1h · CP3 1h                                                                        
- Ảnh tốn thời gian nhất là ảnh nào, vì sao?
ảnh tốn thời gian nhất là ảnh 000000332273.jpg, vì có nhiều người và mỗi người 1 tư thế, tay chân người này dính sang người kia 

## 3. Bảng ca khó (CP1, CP2)

Mỗi điểm bạn phân vân một dòng, nhất là phân vân giữa `v = 1` và `v = 0`, hoặc không chắc hướng người.

| Ảnh | Người / mặt | Điểm | Cờ đã chọn | Phân vân giữa | Lý do chọn |
|---|---|---|---:|---|---|
|000000461002.jpg | người  | right_ear | v=1 | v=1 hay v=2 |cái tai phải của trẻ con nữ đang bị hơi mờ nhưng gióng được từ mắt qua lên em sẽ để v=2 |


## 4. Bảng tự review (CP3)

Đi từ ảnh cuối về ảnh đầu. 5 ảnh người (ít nhất 2 ảnh `back` hoặc `crowd`) và 3 ảnh mặt. Ít nhất 8 dòng, kể cả dòng `ok`. Ghi lỗi trước, sửa sau.

Mã lỗi dùng đúng một trong: `lr_swap`, `vis_flag`, `position`, `missing`, `extra`, `ok`.

| Ảnh | Người / mặt | Điểm | Mã lỗi | Ghi chú | Đã sửa? |
|---|---|---|---|---|---|
|000000332273.jpg | 3 | ok |ok |từ phần hông trở xuống đã gán đúng điểm cảnh báo của script đang nhầm | không cần sửa |
|000000106051.jpg | 2 | right_knee | vis_flag | từ hông phải xuống đầu gối phải phân vân giữa v= 1 và v= 2 ban đầu chọn v=2, sau đổi thành v=1 vì đang bị cỏ che mất ít phần đầu gối  | đã sửa |
|000000461002.jpg	| 2 | right_ear | vis_flag | phân vân giữa v=1 và v=2 ban đầu là chọn v=1 vì tai khá mờ sau chuyển thành v=2 thì có thể thấy tai và gióng từ mắt sang lên chắc chắn là tai | đã sửa|
|000000359340.jpg | 1 | cả người (17 điểm) |lr_swap | dùng skeleton bị ngược | đã sửa |
|000000375535.jpg | 1 |cả người (17 điểm) |lr_swap | dùng skeleton bị ngược| đã sửa|
|face_560526.jpg | 1 | 13 điểm |ok |ok | không cần sửa |
|face_146049.jpg | 1 | 4 điểm mắt |vis_flag | mới đầu để v=2 vì em nghĩ để v=2 được sau khi được BTC giải đáp thì đã sửa sang v=1 vì mình vấn có thể ước lượng vùng mắt |đã sửa |
|face_143959.jpg | 1 |13 điểm |ok |ok | không cần sửa |


Tổng hợp số lỗi theo mã:

| `lr_swap` | `vis_flag` | `position` | `missing` | `extra` | `ok` |
|---:|---:|---:|---:|---:|---:|
|2 |3 |0 | 0| 0| 3|

Điểm còn phân vân giữa `v = 1` và `v = 0` (ghi cả hai lựa chọn và lý do chọn):

sau khi được các anh lab coach giải đáp thì đã không còn phân vân nữa

## 5. Kiểm file xuất và kết quả tự kiểm (CP4)

Tự kiểm tay trong file JSON:

| File | Người / mặt kiểm (ảnh, thứ tự) | Số phần tử `keypoints` | Điểm `outside` ra `v = 0`, `occluded` ra `v = 1`? | `num_keypoints` khớp? |
|---|---|---:|---|---|
| `DangTrungHieu_persons.zip` | `000000106051.jpg`, người #2 | 51 | Có: `right_knee` (occluded) ra `v = 1`; 7 điểm outside ra `v = 0` | Có (10 = số điểm `v > 0`) |
| `DangTrungHieu_persons.zip` | `000000184224.jpg`, người #1 | 51 | Có: `left_ear`, `right_ear`, `right_knee` ra `v = 1`; `right_ankle` ra `v = 0` | Có (16) |
| `DangTrungHieu_faces.zip` | `face_146049.jpg`, mặt #1 | 39 | Có: 8 điểm mắt (occluded) ra `v = 1` | Có (13) |

Sau khi xuất, CVAT ghi `occluded` thành `v = 1` và `outside` thành `v = 0`. Tọa độ của điểm `outside` trong file là `0, 0` hay tọa độ cũ? Tọa độ cũ (cả 78 điểm `v = 0` đều giữ tọa độ cũ, không có điểm nào là 0, 0).

Hai job đã chuyển sang completed trên CVAT? đã chuyển

Dán phần **TÓM TẮT** in ra từ `src/check_submission.py`:

```text
- File person: DangTrungHieu_persons.zip
  Số ảnh: 12 · số skeleton `person`: 16 · mỗi annotation 51 số
  Skeleton theo ảnh: 000000090646=1, 000000103970=1, 000000106051=2, 000000183176=1, 000000184224=1, 000000225138=1, 000000314154=1, 000000332273=3, 000000349521=1, 000000359340=1, 000000375535=1, 000000461002=2
  Cờ v: v=2 193 (71%) · v=1 9 (3%) · v=0 70 (26%)
  num_keypoints trung bình: 12.6
- File face: DangTrungHieu_faces.zip
  Số ảnh: 8 · số skeleton `face`: 8 · mỗi annotation 39 số
  Skeleton theo ảnh: face_105668=1, face_10579=1, face_125051=1, face_143959=1, face_146049=1, face_185015=1, face_261458=1, face_560526=1
  Cờ v: v=2 88 (85%) · v=1 8 (8%) · v=0 8 (8%)
  num_keypoints trung bình: 12.0
- Ghi chú: 78 điểm v = 0 vẫn mang tọa độ cũ (CVAT 2.x xuất như vậy; chuẩn COCO ghi 0, 0). Không phải lỗi: điểm v = 0 bị bỏ qua khi huấn luyện và khi chấm.
- Số [LỖI]: 0 · số [CẢNH BÁO]: 1
Kết quả: ĐẠT (đọc lại từng cảnh báo ở trên)
```

Các `[CẢNH BÁO]` còn giữ nguyên và lý do:
000000332273.jpg #1: cặp ankle nằm ngược phía so với các cặp còn lại. Có thể đổi trái/phải một cặp (`lr_swap`), hoặc tay / chân bắt chéo thật: kiểm lại.
giữ nguyên bởi vì đã kiểm tra và gán nhãn đúng 


## 6. Ảnh chụp màn hình

1. Label `person` trong label constructor (đủ 17 điểm có tên):

   ![Label person](images/1_label_person.png)

Nguồn ảnh: COCO val2017 / Wikimedia Commons.

2. Một người quay lưng đã gán, cờ đã đặt:

   ![Người quay lưng](images/2_nguoi_quay_lung.png)

Nguồn ảnh: COCO val2017 / Wikimedia Commons.

3. Một khuôn mặt đã gán 13 điểm, phóng to vùng mắt:

   ![Khuôn mặt phóng to](images/3_mat_phong_to.png)
   
Nguồn ảnh: COCO val2017 / Wikimedia Commons.

4. Một đoạn JSON xuất của một người:

   ![JSON export](images/4_json_export.png)

Nguồn ảnh: COCO val2017 / Wikimedia Commons.

## 7. Tự đánh giá

1. Lỗi bạn mắc nhiều nhất hôm nay, và cách bạn sẽ tránh ở dự án thật:

   bị mắc nhiều nhất ở phần `occluded` / `outside` cách tránh sẽ là đọc kĩ guideline, không rõ thì hỏi 

2. Một quy tắc bạn đề xuất thêm vào guideline (kèm ảnh ví dụ nếu có):

   không có

3. Nhãn của bạn đi vào model ở đâu? Chọn một lỗi bạn đã sửa và nói nó sẽ làm model học sai thế nào (heatmap, trọng số trong loss, hay bước lật ảnh):

- Heatmap bị “chia đôi”

Model học từ nhiều ví dụ mâu thuẫn: có ảnh left_wrist nằm ở tay trái thật, có ảnh lại nằm ở tay phải. Để giảm loss, heatmap của left_wrist thường có hai đỉnh, ở cả hai tay, hoặc một đỉnh mờ.

Đỉnh sai mạnh hơn: model chọn nhầm tay.
Hai đỉnh gần ngang nhau: điểm dự đoán có thể rơi vào giữa hai tay, không đúng khớp nào.

- Học theo bên của ảnh thay vì bên của người

Lỗi lr_swap hay xảy ra ở người quay lưng, vì người gán quên đổi mẫu, như 2 ảnh back bạn đã sửa. Nếu lỗi này phổ biến, model dễ học một quy tắc sai kiểu “left là bên trái của ảnh”, thay vì bên trái của người. Model sẽ đúng với một hướng nhưng sai hàng loạt khi người quay hướng ngược lại.

- Bước lật ảnh làm lỗi trầm trọng thêm

Khi huấn luyện, ảnh được lật ngang và tên trái/phải được đổi theo. Với nhãn đúng, việc này giúp model hiểu tính đối xứng. Với nhãn đã bị đảo, lật ảnh lại nhân đôi các ví dụ mâu thuẫn, nên model càng khó phân biệt hai bên.

- Điểm đánh giá giảm mạnh

Khi đánh giá bằng OKS, hai điểm bị đảo nằm ở hai bên người, cách vị trí đúng rất xa, nên điểm đó gần như bị tính là sai hoàn toàn. Một người bị đảo cả người có thể bị chấm rất thấp, dù vị trí các khớp đều “đúng chỗ”.
Trong các nghiên cứu phân tích lỗi pose estimation, nhầm trái/phải được xếp thành một loại lỗi riêng (thường gọi là inversion) và là loại lỗi phổ biến, ví dụ trong nghiên cứu của Ronchi và Perona (2017) về chẩn đoán lỗi trên COCO.

- Ảnh hưởng tới ứng dụng thật

Phân tích thể thao: báo nhầm vận động viên dùng chân trái hay chân phải.
Vật lý trị liệu: đếm nhầm bài tập của tay bị thương.
Nhận diện hành động: “giơ tay trái” bị hiểu thành “giơ tay phải”.

## 8. Khó khăn và lỗi kỹ thuật

**1. `lab.py` bị lỗi khi chạy `check` / `setup` 
- Lệnh: `python lab.py check` và `python lab.py setup --mssv 2A202603248 --ten DangTrungHieu`.
- Lỗi: `NotADirectoryError: [WinError 267] The directory name is invalid` ở bước 4 ("Lỗi kẹt Connecting... (Nuclio)"), dòng 110 `shell_in_dir`.
- Nguyên nhân:
  - CVAT được bật bằng `docker compose` trong Ubuntu (WSL), nên thư mục compose là đường dẫn Linux `/home/hieuadmin/cvat-day2`, còn `lab.py` chạy bằng Python trên Windows nên không mở được thư mục này.
  - Máy tôi có cài thêm Nuclio (dùng cho SAM ở Day 3), nhưng bước 4 chỉ tìm container có tên chứa "cvat"/"traefik" nên không nhận ra Nuclio và báo nhầm là tên `nuclio` bị trỏ sai (sang 172.18.0.20, là IP của container Nuclio thật).
- Ảnh hưởng: script dừng trước khi ghi `docker-compose.override.yml` hay sửa `/etc/hosts`; tôi đã kiểm tra lại và CVAT không bị thay đổi gì. Các bước 1–3 (Docker, CVAT 2.74.1, OPA 445 quy tắc) đều [OK].
- Cách xử lý: chạy `python lab.py setup --mssv 2A202603248 --ten DangTrungHieu --bonus --skip-check`.


**2. Cảnh báo của `src/check_submission.py`**
- `[CẢNH BÁO] 000000332273.jpg #1: cặp ankle nằm ngược phía so với các cặp còn lại`.
- Đã kiểm lại trong CVAT: đã kiểm tra lại gán đúng rồi không cần sửa.
- Kết quả cuối của script: 0 lỗi, 1 cảnh báo, ĐẠT.

**3. Điểm cần lưu ý khi đọc file xuất**
- 78 điểm `v = 0` vẫn giữ tọa độ cũ, không về `0, 0` (CVAT 2.x xuất như vậy; script ghi chú đây không phải lỗi).

**4. Khó khăn khi gán nhãn**
- Xác định trái/phải theo người (không theo ảnh), nhất là người quay lưng: mẫu `person` dựng theo người quay mặt nên phải đổi trái/phải.
- Phân vân cờ `v` cho điểm bị che một phần (giữa `v = 1` và `v = 2`), và cách áp quy tắc "ba người ước lượng có gần nhau không".
- Cách đo ngưỡng 60 px để quyết định có gán người nhỏ hay không.
- Thời gian tốn nhiều nhất: 30p

## Bonus (nếu làm)

### B1 — 3 ảnh người khó thêm

| Ảnh | Số skeleton | Số người dưới 60 px | Ca khó nhất |
|---|---:|---:|---|
| `000000065350.jpg` | 2 | không có | không có ca khó |
| `000000161603.jpg` | 1 | có 4 người | ảnh bị ngược sáng và mờ không rõ các khớp của người |
| `000000507223.jpg` | 3 | không có | không có ca khó |

Kết quả `src/check_submission.py` cho `DangTrungHieu_bonus_persons.zip`:

```text
[CẢNH BÁO] 000000161603.jpg #1: các điểm chỉ trải cao 43 px (< 60 px). Người dưới 60 px không gán; nếu người cao hơn nhưng bị cắt khung thì bỏ qua cảnh báo này.
[CẢNH BÁO] 000000507223.jpg #3: cặp ankle nằm ngược phía so với các cặp còn lại. Có thể đổi trái/phải một cặp (`lr_swap`), hoặc tay / chân bắt chéo thật: kiểm lại.

- File person: DangTrungHieu_bonus_persons.zip
  Số ảnh: 3 · số skeleton `person`: 6 · mỗi annotation 51 số
  Skeleton theo ảnh: 000000065350=2, 000000161603=1, 000000507223=3
  Cờ v: v=2 65 (64%) · v=1 5 (5%) · v=0 32 (31%)
  num_keypoints trung bình: 11.7
- File face: DangTrungHieu_bonus_faces.zip
  Số ảnh: 5 · số skeleton `face`: 5 · mỗi annotation 39 số
  Skeleton theo ảnh: face_102517=1, face_317330=1, face_344941=1, face_507166=1, face_68290=1
  Cờ v: v=2 61 (94%) · v=1 0 (0%) · v=0 4 (6%)
  num_keypoints trung bình: 12.2
- Ghi chú: 36 điểm v = 0 vẫn mang tọa độ cũ (CVAT 2.x xuất như vậy; chuẩn COCO ghi 0, 0). Không phải lỗi: điểm v = 0 bị bỏ qua khi huấn luyện và khi chấm.
- Số [LỖI]: 0 · số [CẢNH BÁO]: 2
Kết quả: ĐẠT (đọc lại từng cảnh báo ở trên)
```

### B2 — 5 ảnh khuôn mặt đen trắng / hồng ngoại

Ảnh không màu khó hơn ở điểm nào? Kính râm trên ảnh hồng ngoại có còn là `v = 1` không?

- Ảnh không màu khó hơn ở điểm xác định vùng mắt vì nhiều người có hốc mắt khá sâu, sâu thì sẽ đen sẵn thì với ảnh màu thì nhìn càng khó xác định, 

- Ánh sáng hồng ngoại đi xuyên qua được nhiều loại kính râm, nên trên ảnh hồng ngoại thường vẫn thấy mắt sau tròng kính.
Thấy rõ mắt thì có thể là v = 2. Vẫn tối, không thấy mắt thì là v = 1, như quy tắc với ảnh màu.

### B3 — Model so với nhãn của tôi (không tính điểm)

không làm


## 9. Tài liệu tham khảo và công cụ AI đã dùng

Dùng claude để giải thích về kiến thức về ảnh hồng ngoại, heatmap, OWS 
