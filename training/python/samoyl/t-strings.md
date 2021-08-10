# Строки

[<<`](index.md)

## Немного про числа

- конвертация строк в целое
```
bin_a = '111'
print(int(bin_a))
111
print(int(bin_a,2))
7
print('ff',16)
256
```

## Строки

- многострочная строка
```
'first line\nsecond line'
```
или

```
'''firstline
	 second line'''
```
- конкатенация

```
In [2]: 'sadsad'+'3213213'
Out[2]: 'sadsad3213213'
```
- умножение строк

```
In [3]: '#'*50
Out[3]: '##################################################'
```
Строки -- это упорядоченный неизменяемый тип данных.

```
In [4]: str='interface'

In [5]: str[0]
Out[5]: 'i'

In [6]: str[-1]
Out[6]: 'e'

In [11]: str[5:8]
Out[11]: 'fac'

In [14]: str[:6]
Out[14]: 'interf'

In [15]: str[6:]
Out[15]: 'ace'

In [12]: str[-4:]
Out[12]: 'face'

In [16]: str='123456789'

In [17]: str [::2]
Out[17]: '13579'

In [17]: str [1::2]
Out[18]: '2468'

In [19]: str [::-1]
Out[19]: '987654321'
```

### Некоторые методы для работы со строками

Методы схожи с функциями (именованный блок кода), но в отличие от них методы связаны с конкретным типом объектов.

```
In [1]: str1='hello'

In [2]: type(str1)
Out[2]: str

In [4]: str1.upper()
Out[4]: 'HELLO'
```

Методы  -- это действия, кот можно применять к строкам. Поскольку строки -- неизеняемый тип данных, то все изменяющие строку методы возвращают новую строку, а исходная остается неизменной.

```
In [9]: ip = '10.1.1.1'

In [10]: ip.count('.')
Out[10]: 3

In [14]: ip.find('.')
Out[14]: 2

In [15]: ip.startswith('10')
Out[15]: True

In [7]: ip.replace('10.1','192.168')
Out[7]: '192.168.1.1'

In [12]: iface='\tinterface g0/0\n'

In [13]: iface.strip()
Out[13]: 'interface g0/0'

In [14]: a = '[10,20]'

In [15]: a.strip('[]')
Out[15]: '10,20'

In [2]: str1 = 'This is a string 1,2,3'

In [3]: str1.split()
Out[3]: ['This', 'is', 'a', 'string', '1,2,3']

In [7]: vlans = '2,3,4,100'

In [8]: vlans.split(',')
Out[8]: ['2', '3', '4', '100']

n [21]: if_templ = 'interface {}\nsth-else {}'

In [22]: print(if_templ.format('g0/0', '123'))
interface g0/0
sth-else 123

In [1]: intf = 'g0/0'
In [2]: vlan = '10'
In [3]: mac = 'AAAA:BBBB:CCCC '

In [4]: templ = '{:7}{:<5}{:15}'

In [5]: templ.format(intf,vlan,mac)
Out[5]: 'g0/0   10   AAA:BBBB:CCCC '

In [9]: templ = '{:08b}.{:08b}.{:08b}.{:08b}'

In [10]: templ.format(192,168,0,107)
Out[10]: '11000000.10101000.00000000.01101011'

In [11]: templ = '''
    ...: IP address: {ip}
    ...: Mask:       {mask}
    ...: Interface:  {intf}
    ...: '''

In [14]: print(templ.format(ip='10.1.1.1',intf='g0/0',mask=24))

IP address: 10.1.1.1
Mask:       24
Interface:  g0/0

In [16]: templ = '''
    ...: Информация по адресу: {0}/{1}
    ...:
    ...: IP адрес: {0}
    ...: Маска:    {1}
    ...: '''

In [17]: print(templ.format('10.1.1.1',24))

Информация по адресу: 10.1.1.1/24

IP адрес: 10.1.1.1
Маска:    24
```




