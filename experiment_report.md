# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** AI20K-2A202600762
**Name:** Hoàng Văn Anh
**Date:** 10/06/2026

---

## 1. Ket qua thi nghiem

Chay `agent_simulation.py` voi 2 bo du lieu va ghi lai ket qua:

| Scenario                            | Agent Response                                                   | Accuracy (1-10) | Notes |
| ----------------------------------- | ---------------------------------------------------------------- | --------------- | ----- |
| Clean Data (`processed_data.csv`) | Based on my data, the best choice is Laptop at $1200.            | 10              |       |
| Garbage Data (`garbage_data.csv`) | Based on my data, the best choice is Nuclear Reactor at $999999. | 10              |       |

---

## 2. Phan tich & nhan xet

### Tai sao Agent tra loi sai khi dung Garbage Data?

Garbage data co nhieu van de co the lam sai ket qua cua Agent. Trong `garbage_data.csv` co duplicate ID (`id=1` xuat hien hai lan), gia khong hop le (`"ten dollars"` thay vi mot so), gia bang 0 va category rong. Những record nay khong bi loai bo se lam nham luan logic chon san pham cao nhat theo category.

Agent dong thoi rat don gian: no chon san pham electronics co gia lon nhat. Do do, khi co `Nuclear Reactor` voi gia 999999 va category `electronics`, Agent phan hoi sai du neu du lieu khong duoc validate ky. Outlier lon, gia khong phai so va category trong se lam thiet lap tri tue nhan tao “hieu” sai ve tap du lieu.

---

## 3. Ket luan

**Quality Data > Quality Prompt?**

Dong y. Quality data quan trong hon quality prompt vi neu du lieu dau vao co loi, Agent se dua ra ket qua sai hoac khong the dua ra ket qua chinh xac, du cho prompt duoc viet tot. Du lieu sach va duoc validation thuc hien dung giup phong ngua nhung ket qua qua lai tu garbage data.
