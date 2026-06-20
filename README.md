## Nguyễn Nguyệt Linh

## Lớp: K58KTP.K01

## Học phần: Kiểm thử phần mềm

## Giảng viên hướng dẫn: TS. Nguyễn Tuấn Linh

## Giới thiệu

## Đây là chương trình thực nghiệm cho đề tài 68: "Spectrum-Based Fault Localization và Suspiciousness Score"

được thực hiện trong học phần **Kiểm thử phần mềm**.

# Link YouTube 

Mục tiêu của dự án là mô phỏng kỹ thuật Spectrum-Based Fault Localization (SBFL) nhằm xác định vị trí lỗi trong chương trình dựa trên:

- Coverage Information
- Kết quả Pass/Fail của các test case
- Suspiciousness Score

Hai công thức được sử dụng:

- Tarantula
- Ochiai

---

## Bài toán thực nghiệm

Chương trình thực hiện chức năng xếp loại học lực sinh viên theo GPA hệ 4.

Quy tắc xếp loại:

| GPA | Xếp loại |
|-------|----------|
| GPA < 2.0 | Yếu |
| 2.0 ≤ GPA < 2.5 | Trung bình |
| 2.5 ≤ GPA < 3.2 | Khá |
| 3.2 ≤ GPA < 3.6 | Giỏi |
| GPA ≥ 3.6 | Xuất sắc |

Một lỗi logic được cố tình đưa vào chương trình để phục vụ việc nghiên cứu kỹ thuật Fault Localization.

---

## Cấu trúc dự án

```text
KTPM_Project/
│
├── ktpm-1.ipynb
├── README.md
├── screenshots/
│   ├── coverage_matrix.jpg
│   ├── diagnosis_matrix.jpg
│   ├── tarantula_result.jpg
│   └── ochiai_result.jpg
│
└── report/
    └── KTPM3.pdf
```

---

## Bộ kiểm thử

| Test Case | GPA | Expected |
|------------|------|-----------|
| T1 | 3.8 | Xuất sắc |
| T2 | 3.4 | Giỏi |
| T3 | 2.9 | Khá |
| T4 | 2.2 | Trung bình |
| T5 | 2.1 | Trung bình |
| T6 | 1.8 | Yếu |

---

## Coverage Matrix

| Statement | T1 | T2 | T3 | T4 | T5 | T6 |
|------------|----|----|----|----|----|----|
| S1 | 1 | 1 | 1 | 1 | 1 | 1 |
| S2 | 0 | 1 | 1 | 1 | 1 | 1 |
| S3 | 0 | 0 | 1 | 1 | 1 | 1 |
| S4 | 0 | 0 | 0 | 1 | 1 | 0 |
| S5 | 0 | 0 | 0 | 0 | 0 | 1 |

---

## Diagnosis Matrix

| Statement | T1 | T2 | T3 | T4 | T5 | T6 |
|------------|----|----|----|----|----|----|
| S1 | 1 | 1 | 1 | 1 | 1 | 1 |
| S2 | 0 | 1 | 1 | 1 | 1 | 1 |
| S3 | 0 | 0 | 1 | 1 | 1 | 1 |
| S4 | 0 | 0 | 0 | 1 | 1 | 0 |
| S5 | 0 | 0 | 0 | 0 | 0 | 1 |
| Result | P | P | P | F | F | P |

---

## Kết quả Tarantula

| Statement | Score |
|------------|--------|
| S1 | 0.500 |
| S2 | 0.571 |
| S3 | 0.667 |
| S4 | 1.000 |
| S5 | 0.000 |

---

## Kết quả Ochiai

| Statement | Score |
|------------|--------|
| S1 | 0.577 |
| S2 | 0.632 |
| S3 | 0.707 |
| S4 | 1.000 |
| S5 | 0.000 |

---

## Kết quả

Cả hai công thức Tarantula và Ochiai đều xác định:

```text
S4 = Statement nghi ngờ cao nhất
```

Đây chính là câu lệnh chứa lỗi trong chương trình.

---

## Công nghệ sử dụng

- Python 3.x
- Jupyter Notebook
- Fault Localization
- Software Testing

---
