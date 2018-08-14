# UsbKeyboardDataHacker

USB键盘流量包取证工具 , 用于恢复用户的击键信息

## example

### Description :

```
Usage : 
        python UsbKeyboardHacker.py data.pcap
Tips : 
        To use this python script , you must install the tshark first.
        You can use `sudo apt-get install tshark` to install it
Author : 
        Angel_Kitty <angelkitty6698@gmail.com>
        If you have any questions , please contact me by email.
        Thank you for using.
```

### Demo :

```
1. Step1 , Get data

root@kali:~/桌面/usb/USB/UsbKeyboardDataHacker# tshark -r ./example.pcap -T fields -e usb.capdata
00:00:09:00:00:00:00:00
00:00:00:00:00:00:00:00
00:00:0f:00:00:00:00:00
00:00:00:00:00:00:00:00
00:00:04:00:00:00:00:00
00:00:00:00:00:00:00:00
00:00:0a:00:00:00:00:00
00:00:00:00:00:00:00:00
20:00:00:00:00:00:00:00
20:00:2f:00:00:00:00:00
...


2. Step2 , decode

root@kali:~/桌面/usb/USB/UsbKeyboardDataHacker# python UsbKeyboardDataHacker.py ./example.pcap 
[-] Unknow Key : 01
[-] Unknow Key : 01
[+] Found : flag{pr355_0nwards_a2fee6e0}
```

## Cryptanalysis of the Autokey Cipher

### Demo :

```
root@kali:~/桌面/usb# python break_autokey.py 
-824.697138698 autokey, klen 3 :"YCI", ONDDICCUXCERSFORFKKSWPDHRNTDERUVXRPRUGCAZZLSOYMESWPEESTJAPAXANPPYDSEGJPSYKMCBCEUGWGCWMNPTUWMYATGHQHVBPMSTBATZMIWSPTHTG
-772.470967688 autokey, klen 4 :"SYNR", URYABOHCYQRMWTOXOFNASUIDOWSRDOFILXFGAYOOFDXDIGHPICMHSFLGADYRPKOYWITENTAUUGEGRICPRSYTBARSEHUNOPLRTUCLYCFIKLNEQBOROWBIUD
-803.48764464 autokey, klen 5 :"BCGKY", LNFHXUSXSHEWXRYFOBKZBLUTHPPAYDIKONHGBHGNZAELAKEOFIJSMCPEAWHILNQIDHUMBYMEVYGOHTIPUTHADYWEFENJORBRYVWBAYMXHNUADFOBEUKLHV
-761.616653993 autokey, klen 6 :"KIDAHF", CHIROADVRNKOROOWAKKJSDVTWHIRWRBSGUOXKDNAREBOAJNOPUTNNTITZVWEHUNUPOAIWHEKHRITHEZEAHTETOPEMDSRDSTBPSKKYVSBYDURILDSKGHOFH
-743.720273262 autokey, klen 7 :"KIDEAFY", CHINVAHASWLTUCFRONIDEUEPTIXQXGIGGOURFNNORHUMAWQBJOHWERWEEBNTYRILKFOESTIOCLAISGSTXASQMAWOFPVTSARZSOUKRFIBUTIVVEABLPUEEZ
-674.914569565 autokey, klen 8 :"FLAGHERE", HELLOBOYSANDGIRLSYOUARESOSMARTTHATYOUCANFINDTHEFLAGTHATIHIDEINTHEKEYBOARDPACKAGEFLAGISJHAWLZKEWXHNCDHSLWBAQJTUQZDXZQPF

```
