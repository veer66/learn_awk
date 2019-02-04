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
