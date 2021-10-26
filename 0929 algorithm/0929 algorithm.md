# 1. 단순 2진 암호코드

```
입력

2
16 80
00000000000000000000000000000000000000000000000000000000000000000000000000000000
00000000000000000000000000000000000000000000000000000000000000000000000000000000
00000000000000000000000000000000000000000000000000000000000000000000000000000000
00000000000000000000000000000000000000000000000000000000000000000000000000000000
00000000000000000000000000000000000000000000000000000000000000000000000000000000
00000000000000000000000000000000000000000000000000000000000000000000000000000000
00000000000000011101101100010111011011000101100010001101001001101110110000000000
00000000000000011101101100010111011011000101100010001101001001101110110000000000
00000000000000011101101100010111011011000101100010001101001001101110110000000000
00000000000000011101101100010111011011000101100010001101001001101110110000000000
00000000000000011101101100010111011011000101100010001101001001101110110000000000
00000000000000011101101100010111011011000101100010001101001001101110110000000000
00000000000000011101101100010111011011000101100010001101001001101110110000000000
00000000000000000000000000000000000000000000000000000000000000000000000000000000
00000000000000000000000000000000000000000000000000000000000000000000000000000000
00000000000000000000000000000000000000000000000000000000000000000000000000000000
11 70
00000000000000000000000000000000000000000000000000000000000000000000000
00000000000000000000000000000000000000000000000000000000000000000000000
00000001100101000110100011010111101101110010011001001101110110000000000
00000001100101000110100011010111101101110010011001001101110110000000000
00000001100101000110100011010111101101110010011001001101110110000000000
00000001100101000110100011010111101101110010011001001101110110000000000
00000001100101000110100011010111101101110010011001001101110110000000000
00000001100101000110100011010111101101110010011001001101110110000000000
00000000000000000000000000000000000000000000000000000000000000000000000
00000000000000000000000000000000000000000000000000000000000000000000000
00000000000000000000000000000000000000000000000000000000000000000000000

출력
#1 38
#2 0
```

```
t = int(input())

for cnt_t in range(1, t + 1):
    n, m = map(int, input().split())

    for _ in range(n):
        datas = input()
        if int(datas):
            key_data = datas

    key_data = list(key_data)


    for _ in range(m):
        if int(key_data[-1]):
            break
        else:
            key_data.pop()
    tmp_datas = list()
    real_datas = list()
    for _ in range(8):
        data_lst = list()
        for _ in range(7):
            data_lst.append(key_data.pop())
        data = ''
        for tmp in range(6, -1, -1):
            data += data_lst[tmp]
        tmp_datas.append(data)

    for _ in range(8):
        real_datas.append(tmp_datas.pop())



    dic_secret = {
        '0001101': 0,
        '0011001': 1,
        '0010011': 2,
        '0111101': 3,
        '0100011': 4,
        '0110001': 5,
        '0101111': 6,
        '0111011': 7,
        '0110111': 8,
        '0001011': 9,
    }

    datas_sum = 0

    result = 0
    for num in range(0, 8):
        if num % 2:
            datas_sum += dic_secret[real_datas[num]]
            result += dic_secret[real_datas[num]]
        else:
            datas_sum += dic_secret[real_datas[num]] * 3
            result += dic_secret[real_datas[num]]

    if not datas_sum % 10:
        print('#{} {}'.format(cnt_t, result))
    else:
        print('#{} '.format(cnt_t), end='')
        print('0')
```
