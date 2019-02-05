# learn_awk

วิธีใช้ awk อย่างง่าย 

## ไฟล์ pm25.csv

```
time usage,pm2.5 (mi),pm2.5 (sharp)
0m,50 mg/m3,45 mg/m3
5m,28 mg/m3,33 mg/m3
10m,18 mg/m3,18 mg/m3
```

## แสดงข้อมูล column แรกด้วย awk

```
# -F, เป็นตัวบอกว่าใช้ , (comma) แบ่ง field
# $1 คือให้พิมพ์ field ที่ 1
$ cat pm25.csv | awk -F, '{ print $1 }'
```

ผลที่ได้

```
time usage
0m
5m
10m
```

## แสดงข้อมูล column ที่สองด้วย awk

```
$ cat pm25.csv | awk -F, '{ print $2 }'
```

ผลที่ได้

```
pm2.5 (mi)
50 mg/m3
28 mg/m3
18 mg/m3
```

## ใช้ gsub เปลี่ยนแปลงข้อมูล m ของแต่ละบรรทัดเป็น minute(s) แล้วแสดงผล

```
# gsub แทนค่า /m/ (regular expression) ใน $1 ด้วย minute(s) แล้วก็เอาไปเก็บใน $1 เหมือนเดิม
$ cat pm25.csv | awk -F, '{ gsub(/m/, "minute(s)", $1); print $1 }'
```

ผลที่ได้

```
timinute(s)e usage
0minute(s)
5minute(s)
10minute(s)
```

เพิ่มช่องว่าง

```
cat pm25.csv | awk -F, '{ gsub(/m/, " minute(s)", $1); print $1 }'

```
ผลลัพธ์

```
ti minute(s)e usage
0 minute(s)
5 minute(s)
10 minute(s)
```

ใช้ tail ช่วยตัด head ออก

```
cat pm25.csv | tail -n +2 | awk -F, '{ gsub(/m/, " minute(s)", $1); print $1 }'
```

ผลลัพธ์

```
0 minute(s)
5 minute(s)
10 minute(s)
```
