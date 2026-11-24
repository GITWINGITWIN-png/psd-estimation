# Periodogram, Bartlett และ Welch

**English summary:** a teaching notebook (in Thai) on power spectral density estimation from first principles. It derives the periodogram, Bartlett and Welch estimators, proves their bias and variance, and checks every proof numerically, ending with a Monte Carlo comparison of bias, variance and MSE and a check of `scipy.signal` against code written from scratch. It uses only NumPy, SciPy and Matplotlib on synthetic signals, and all 26 figures are embedded, so it can be read without running it.

โน้ตบุ๊กสอนเรื่อง **การประมาณค่าความหนาแน่นสเปกตรัมกำลัง (Power Spectral Density Estimation)**
ตั้งแต่พื้นฐาน พร้อมการพิสูจน์ทางคณิตศาสตร์ และกราฟประกอบ 26 ภาพ

📓 **[periodogram.ipynb](periodogram.ipynb)** มี 58 เซลล์ รันครบและฝังผลลัพธ์ไว้แล้ว

## เปิดดู

```bash
uv run jupyter lab periodogram.ipynb
```

หรือเปิดไฟล์ `.ipynb` ใน VS Code ได้เลย (กราฟทั้งหมดฝังอยู่ในไฟล์แล้ว ไม่ต้องรันใหม่)

## รันใหม่ทั้งหมด

```bash
uv run jupyter nbconvert --to notebook --execute --inplace periodogram.ipynb
```

## เนื้อหาโดยย่อ

โน้ตบุ๊กตอบคำถามเดียว: *มีข้อมูลแค่ $N$ จุด จะบอกได้แค่ไหนว่ากำลังของสัญญาณอยู่ที่ความถี่ไหน?*

1. **พื้นฐาน:** สัญญาณ การสุ่ม และจาก DTFT ไปเป็น DFT
2. **ACF และ PSD:** ทฤษฎีบท Wiener–Khinchin
3. **Periodogram:** พิสูจน์ว่ามันคือ DTFT ของ ACF แบบ biased
4. **คุณสมบัติทางสถิติ:** พิสูจน์ bias (Fejér kernel) และ variance
   ผลคือ periodogram **ไม่ใช่ตัวประมาณที่ consistent** (ผิดพลาด 100% เสมอ)
5. **Leakage และหน้าต่าง:** Dirichlet kernel และการแลกกันระหว่าง resolution กับ dynamic range
6. **Bartlett:** หั่นเป็น $K$ ท่อนแล้วเฉลี่ย และพิสูจน์ $\mathrm{Var} = S^2/K$
7. **Welch:** ใส่หน้าต่างและ overlap แล้วพิสูจน์ตัวประกอบ $U$ และสูตร variance
8. **เปรียบเทียบ:** วัด bias², variance และ MSE ด้วย Monte Carlo
9. **ใช้งานจริง:** `scipy.signal` พร้อมตรวจกับโค้ดที่เขียนเอง
10. **สรุป:** ตารางเทียบและแนวทางเลือกใช้

> ทุกการพิสูจน์มีเซลล์โค้ดที่ยืนยันผลด้วยตัวเลขตามมาเสมอ

## สิ่งที่ต้องมี

Python 3.12 ขึ้นไป จัดการด้วย [uv](https://docs.astral.sh/uv/) และใช้ `numpy`, `scipy`, `matplotlib` กับ `jupyter`

ฟอนต์ **Noto Sans Thai** (สำหรับข้อความไทยในกราฟ):

```bash
sudo apt install fonts-noto-core   # Debian/Ubuntu
```

---

พัฒนาโดยมี AI coding assistants ช่วย (built with help from AI coding assistants)
