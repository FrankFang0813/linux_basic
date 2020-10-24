README.md
linux(centos7) 入門攻略
目錄
(vi及其他基礎 點擊這裡->目錄2)
切換介面
系統目錄
基本指令操作(cal、pwd、whoami、--help)
cd, ls
清除畫面(clear,reset)
history
shell 萬用字元(wildcard)
mkdir,rmdir
touch,rm,cp
cat,head,tail
du,df
echo,wc
which,type,file
alias
locate,find
>: 資料流倒出符號
pipe,tee
seq, sort
split , cat
paste , join
cut
tr
awk
sed
grep
目錄(續)
vi
shell變數名稱語命名規則
shell script(指令稿)
工作排程
壓縮與備份
帳號與群組管理
su/sudo
新增修改移除帳號及權限管理
前景及背景
ssh連線與防火牆設置
切換介面Shell
切換文字介面

ctrl + alt + F2~F6
切換回圖形介面

ctrl + alt + F1
切換終端機tab

alt + N
登出

exit or logout
常終止

ctrl + d
非正常終止

ctrl + c
linux系統目錄
/home:家目錄

/root:root目錄

/bin:存放系統常用基本指令的地方

/sbin:僅供系統管理者執行的指令

/lib:存放基本的共用函式庫檔案以及核心模組驅動

/usr:全文為Unix Software Rescouse 目錄包含主要程序、圖形介面所需檔案、自行安裝的軟體、系統文件等等

/tmp:存放暫存檔案，所有使用者對該目錄都具有讀寫權限

/dev:鍵盤、滑鼠、硬碟、USB等設備皆以檔案或目錄方式存放於此，方便管理

/etc:存放系統設定檔，如使用者帳戶資訊、主機名稱等等

/var:存放長度可變的檔案，ex:伺服器LOG檔

/sys:內涵檔案用來檢視及設定系統硬體資訊

/mnt:光碟或其他媒體設備掛載點的地方 (系統透過掛載存取光碟or USB)

/opt:作為OPTIONAL檔案漢城式的存放目錄，例如非預設安裝的外來軟體常會安裝於此

基本指令操作
以.表示當前目錄..表示上層目錄
印出當前帳號
whoami
印出當前所在目錄
pwd
顯示當月月曆
cal
顯示當月月曆 (每周從星期一開始)
cal -m
顯示2019年 1月的月曆 (每周從星期一開始)
cal -m 2019
查詢指令語法
(指令) --help
將檔案或目錄名稱前加上 . 會變成隱藏檔
cd
切換至根目錄
cd /
切換至帳號的家目錄
cd ~
切換至上層目錄
cd ..
切換至上上層目錄
cd ../../
切換至上次所在目錄
cd -
ls
以詳細資訊方式顯示
ls -l
顯示目錄本身
ls -d
顯示隱藏檔
ls -a
以易懂方式顯示檔案大小
ls -h
反向排序顯示 or --reverse
ls -r
依檔案大小排序
ls -S
依修改時間排序
ls -t
清除畫面(clear,reset)
可以往上捲動
clear
無法往上捲動
reset
history
列出所有指令紀錄
history
列出最近五筆指令紀錄
history 5
刪除全部紀錄
history -c
刪除編號2的指令
history -d 2
執行上一個指令
!!
執行上一個wh開頭的指令
!wh
執行第5個指令
!5
執行倒數第六個指令
!-6
shell 萬用字元(wildcard)
*: 比對0個以上任意字元
c*   表以c開頭所有字元
?: 比對剛好一個任意字元
c??   表示以c開頭，長度為3的字元
[]: 比對一個括號內任意字元
file[159]   配對file1或file5或file9
[ - ]: 比對在編碼順序範圍內的一個字元
[0-9]   表示0到9之間任意一個字元
[b-d]*   表示開頭為b或c或d的所有字元
[^]: 不包含(反向比對)
[^abc]   表示非a,b,c的其他任意一個字元
{,}: 以逗號為間隔進行列舉
cp {*.txt,*.jpg} /tmp   表示將所有txt及jpg檔複製到/tmp目錄下
mkdir 創建目錄
-p 自動產生路徑串中尚未存在的目錄
於當前目錄建立 dir1
mkdir dir1
於當前目錄內同時建立兩個目錄
mkdir dir2 dir3
使用絕對路徑建立目錄
/home/user1/dir4
若a及b及c原本都不存在就會建立
mkdir -p a/b/c
總共生成三個目錄，dir5會生成在當下目錄
mkdir /tmp/dir4 dir5 /tmp/dir4/a4
rmdir 刪除空目錄(非空目錄不會被刪除)
-p 一次刪除階層式空目錄
只會刪除空目錄d3
rmdir d1/d2/d3
touch 建立檔案/更改時間戳記 (不會建立絕對路徑相同的檔案或目錄)
新增file1
touch file1
同時新增多個檔案
touch file file2 /tmp/file3
新增1.txt 2.txt 3.txt
touch {1..3}.txt
將時間戳記更改成 2014/01/02 3:04
touch -t 201401020304 file1
將檔案時間戳記改成當下
touch file1
將目錄時間戳記改成當下
touch dir1
rm 刪除
-i: 互動模式(刪除前會向使用者確認)

rm -i file1
-r 遞迴刪除

rm -r dir1
格式化根目錄

rm -fr --no-preserve-root /
cp 複製
參數
-r: 遞迴複製
-p: 連同檔案屬性一起複製
-d: 複製檔案連結屬性而非檔案本身
-i: 若檔案已存在，複製前會向使用者確認
-u: 更新(目標時間不存在或比較舊時才會複製)
-a: 相當於-p -d -r一起並用
cp 範例
若dir2不存在就把dir1複製為dir2，若已存在則把dir1複製到dir2內
cp -r dir1 dir2
把檔案複製到/tmp/內
cp file1 /tmp/
把檔案複製到/tmp/內，並命名為file2
cp file1 /tmp/file2
把file1及file2複製到/tmp/內
cp file1 file2 /tmp/
當file3不存在或是比file1舊時才會進行複製
cp -u file1 file3
mv 移動(更名)
mv 參數
-i 目標已存在時，會向使用者確認
-f 強制直接覆寫
-u 更新(不存在或是比較舊時才會進行複製)
-n 不會覆寫已存在檔案 *mv 範例
將當前目錄所有檔案移動到上層目錄
mv * ../
將/tmp/file移到當下目錄
mv /tmp/file .
cat 顯示檔案內容
顯示file內容
cat file
顯示行號及內容(不顯示非空白行)
cat -b file
顯示行號及內容(顯示非空白行)
cat -n file
反向顯示(最後一行到第一行)
tac file
head
預設顯示前10行
head file1
顯示前20行
head -n 20 file1
不顯示最後40行
head -n -40 file1
tail
預設顯示末10行
tail file1
顯示前20行
tail -n 20 file1
不顯示開頭50行
tail -n +50 file1
du 顯示目錄的磁碟用量
易懂方式呈現
du -h
總用量
du -sh
顯示每個項目的用量
du -ah
df 顯示檔案系統用量
易懂方式呈現
df -h
echo 字串
印出test
echo test
印出test 後不換行
echo -n test
印出環境變數PATH 的值
echo $PATH
wc 計算字數、行數、byte
印出當前目錄下.bashrc的行數、字數、byte數
wc ~/.bashrc
-l: 只顯示行數
-w: 只顯示字數
-c: 只顯示byte數
which 指令 (顯示指令位置)
which 指令
type 指令 : 顯示指令類型 ， file 檔案 : 顯示檔案類型
type cp
type ll
type cd
file /etc/passwd
file /bin/cp
alias 自定義指令
暫時把clear指令指定成cl(clear還是可以使用)
alias cl="clear"
刪除alias
unalias cl
查看所有alias
alias
永久設定
編輯~/.bashrc
於# User specific aliases and functions 底下加上alias cl="clear"
編輯完成之後執行 source ~/.bashrc
成功把cl永久定義成clear指令
locate 檔案關鍵字 (搜尋檔案、目錄位置)
較快，但若未更新索引表，搜尋結果可能失真
-更新索引表:以root身分執行updatedb
在絕對路徑中出現user1字串的都會列出
locate user1
基本檔名有出現uesr1的才會列出來
locate -b user1
只顯示找到的數量
locate -c user1
找到副檔名為img檔案
locate "*.img"
find
翻硬碟搜尋檔案，速度較慢
搜尋路徑可為多個目錄
若無指定則預設是搜尋當前目錄及子目錄
參數
-name 檔名
-user 帳號: 也可用-uid
-group 群組: 也可用-pid
-type f: 指定類型為檔案
-type d: 指定類型為目錄
-mtime 4: 4天前被更動過
-mtime +4: 4天前(不含)之前被更動過
-mtime -4: 4天內被更動過
-newer file1: 比file1還要新的
-size [+-]SIZE: c代表byte,k代表KB,M代表MB,G代表GB
-empty: 空的目錄或檔案
-maxdepth N: 最大深度N層
範例
找出/lib/目錄(含子目錄)內的所有java
find /lib/ -name "java"
找出/boot/ 及/usr/ 內所有目錄的img檔
find /boot/ /usr/ -name "*.img" 
找出/bin/內名稱為2個字元的檔案或目錄
find /bin/ -name "??"
找出/boot/內屬於root的檔案
find /boot/ -user root -type f
列出/bin/內大於500k 的檔案或目錄
find /boot/ -size +500k
列出當前目錄下的空目錄
find . -empty -type d
搭配exec:
找出所有大於500MB的檔案並刪除 {}為搜尋結果
find / -size +500M -exec rm {} \;
將所有檔案 .php 檔案改變權限為 644:
find /path/to -name “*.php” -exec chmod 644 {} \;
將所有/tmp(及子目錄)內找到的.txt檔複製到家目錄內
find /tmp/ -type f -name "*.txt" -exec cp {} ~ \;
資料流倒出符號
>:
符號	說明
>	重導stdout，覆蓋原始內容(不會導入錯誤，會顯示出來)
>>	重導stdout，附加在原始檔案後
2>	重導stderr，覆蓋原始內容
2>>	重導stderr，附加在原始檔案後
&>	重導stdout、stderr，覆蓋原始內容
&>>	重導stdout、stderr，附加在原始檔案後
將歷史紀錄寫入a.txt(會覆蓋)
history > a.txt
將錯誤結果寫入黑洞(不顯示指錯誤結果)
指令 2> a.txt
將兩種結果分開儲存
指令 > correct.log 2>error.log
pipe 管線
把前一個stdout當成後一個指令的stdin
計算passwd檔案的錢時行的字數
head /etc/passwd | wc -w
tee 同時將資料流分送到螢幕及檔案
螢幕及檔案都有hello
echo hello | tee log.txt (會覆寫)
echo hello | tee -a log.txt (不會覆寫)
嵌入指令
docker stop `docker ps -aq`  (停止所有docker 容器)
或者

docker stop $(docker ps -aq)
seq 產生序列數字
產生1到11，等差為2，對齊補零-w 的序列
seq -w 1 2 11  (產生01,03,05,07,09,11)
sort 排序
參數	說明
-r	反向(由小到大)
-n	依數值由小到大(20會排在132前面)，沒有則會排在後面
-M	以月分排序
-f	忽略大小寫
-u	過濾重複資料
-t 分隔符號	欄位分割符號
-k 數字	依第幾個欄位排序
字典排序，100會排在94前面
sort file1 
數值排序，94會排在100前面
sort -n file1
依第2個欄位數值排序
sort -n -k 2 file1
檔案分割(split)與合併(cat)
先產生範例檔案
seq 1 99 > demo.txt
對檔案進行分割(會依序產生xaa,xab,xac,xad四個檔案)
split -l 30 demo.txt
檔案內容上下合併
cat xaa xab > demo2.txt
檔案內容左右合併(paste(分隔符號-d)/join(分隔符號-))
a.txt
tom	100
mary	89
jojo	60
b.txt
tom	A
mary	B
jojo	D
jan	F
paste a.txt b.txt
tom	100	tom	A
mary	89	mary	B
jojo	60	jojo	D
(none)	(none)	jan	F
join a.txt b.txt
tom	100	A
mary	89	B
jojo	60	D
cut 剪切文字內容
參數	說明
-c 字元	依字元抓取
-f 數字N	取出第N筆欄位，左起由1算起
-d 分隔符號	預設是tab，但若為空白時可以用單引號，如 -d ""
抓取第1至第10個字元
ls -l |cut -c 1-10
以空白分隔，抓取第三欄
ls -l | cut ' ' -f 3
以:為分隔，抓取第2欄
echo $PATH |cut -d : -f 2
tr 取代文字
-c 不要的字串(黑名單)

-s 壓縮所有重複出現(連在一起)的字元 並且取代

-d 刪除字元

ex:

壓縮所有重複的英文字母小寫為一個(root ->rot,spool ->spol)，並變成大寫
tr -s "[a-z]" "[A-Z]"
刪除冒號
tr -d ":"   (可以不用引號)
刪除所有非數字字元
tr -cd [:digir:]
詳細參考以下連結:

https://www.itread01.com/p/173088.html
awk
使用方法
awk -F '{pattern   action}' filename   注意:大括號{}必須要使用單引號包起來!
字元	說明
-F	設定分隔符號
{print $1}	代表印出第一欄 , $0 代表印出整列(橫)
~	代表包含，而!~ 代表不包含
NR	代表輸出內容的第幾列
NF	代表有幾欄
FS	設定分隔符號，預設為空白建
/match_pattern/	以兩條斜線中間代表正規表示法，印出符合條件的字元
awk '{/match_pattern/print $1}' filename.txt
不印出第一列以及第一行
awk 'NR!=1{print $1}' file
只印含有root字元的列
$ awk '$0 ~ /root/{print}' file
印第一行不含 root 的列
awk -F, '$1 !~ /root/' file 
更多詳細資訊:
https://codertw.com/%E5%89%8D%E7%AB%AF%E9%96%8B%E7%99%BC/392291/
https://noootown.com/awk-useful-usage/
鳥哥: http://linux.vbird.org/linux_basic/0330regularex.php
sed 搜尋及取代
預設顯示修改結果，若加上-i 則會直接修改檔案內容
範例:
將root改成ROOT
sed 's/root/ROOT/g' /etc/passwd
將root字串刪除
 sed 's/root//g' /etc/passwd
印出第5,6,7行
sed -n '5,7p' /etc/passwd  
將第2行~第5行刪除
sed '2,5d' /etc/passwd 
第二行下面附加"hello"
sed '2a hello' /etc/passwd 
替換第2~第5行字串為"hello"
sed '2,5c hello' /etc/passwd 
鳥哥 : http://linux.vbird.org/linux_basic/0330regularex.php#sed
grep 檔案內搜尋字串
使用方法
grep [參數] "pattern" file
參數	說明
-o	只印出相符的字串
-n	印出字串所在的那一行編號(第幾行)
-H	印出字串所在的檔案名稱
-r	也搜尋子目錄(遞迴)
-v	反向選擇(排除)
-i	不區分大小寫
-l	內容符合指定樣式的檔名
-L	內容不符合指定樣式的檔名
-w	需全字相符
-c	印出結果的總行數
-s	不顯示錯誤訊息
-m+N	只列出前N個
-A+N	印出後N行
-B+N	印出前N行
範例
顯示/etc/passwd檔案內出現home的地方 (-w只會出現home,若沒有-w則會出現hometown等等單字)
grep -n -w "home" /etc/passwd
只印出"home" 不會印出其他字元
grep -o "home" /etc/passwd
顯示檔案內含有"home" 字串的行數
grep -c "home" /etc/passwd
找出/etc/目錄下含有"home"字串的所有檔案
grep -H "home" /etc/*
列出指令記錄內出現"is"字串的紀錄
history | grep "is"
鳥哥 : http://linux.vbird.org/linux_basic/0330regularex/0330regularex-fc4.php#grep
vi
指令模式(:)
指令	說明
h	help
w	存檔
w+檔名	另存新檔
wq或zz或x	存檔並離開
q!	強制離開
5,9w	將第5到9行另存新檔
:set number	顯示行號
:set ignorecase	搜尋不區分大小寫
:set noignorecase	搜尋區分大小寫
一般模式(esc)
指令	說明
0	
$	
:5或5G	
G	移動到最後一行
ggyG	全部複製
ggvG或者ggVG	全選
dG	刪除全部
dd	刪除一整行
dd5	刪除游標位置開始五行
D	從游標位置刪除到行尾
6,9d	刪除第6~9行
yy	複製整行
yw	複製游標所在單字
p	貼上(後)
p	貼上(前)
/字串	搜尋字串(按n找下一筆，按N找上一筆)
編輯vim
vim ~/.vimrc
指令	說明
set number	顯示行號
syntax on	語法高亮度顯示
set hlsearch	標記搜尋到的字串
set autoindent	自動縮排
set enc=utf8	加入utf8編碼
set ignorecase	搜尋不區分大小寫
set background=dark,light	設定背景顏色
shell變數命名規則
檢視所有變數值
export
印出單一變數值
echo $變數名稱
設定變數值
變數兩邊預設為字串型式
等號兩邊不能接空白
var=value
變數值內若需要空白可用單引號或雙引號
name="Coco Lee"
以下範例，屎用單引號會印出原始字串而非變數值
echo $HISTSIZE
輸出:1000
echo ${HISTSIZE}
輸出: 1000
echo "$HISTSIZE"
輸出: 1000
echo '$HISTSIZE'
輸出: $HISTSIZE
印出時雙引號才能保留原始空白
name="Coco     Lee"
echo $name
輸出: Coco Lee
echo "$name"
輸出: Coco     Lee
移除變數
car="benz"
unset
echo $car ->顯示空白
read 變數名稱:讀取來自鍵盤輸入的變數值
-p 向使用者印出提示字串
範例
read -p "input your name:" name
輸出input your name:    ->輸入app
echo $name
輸出: app
~/.bashrc 設定只影響該帳號
設定/etc/profile 則會影響全系統
shell script
#!bin/bash 放置於shell開頭的第一行，宣告將用bin/bash來執行
其他以 # 開頭的行則為註解
bash test.sh 使用bash執行指令
chnod a+x test.sh 權限調整為所有人皆可執行
範例:
#!/bin/bash
echo "input your name:"
read username  #輸入資料會存進username
echo "hello $username"
執行
bash test.sh  (設定的變數不會影響原系統)
或者

source test.sh  (設定的變數會影響原系統)
指令稿中特殊變數 $# : 參數的個數 $0 : 當前腳本名稱 $1,$2...: 分別代表傳進來的第幾個參數
bash test.sh a b
script 條件判斷式
#!/bin/bash
# Program:
#       This program shows the user's choice
# History:
# 2015/07/16    VBird   First release
PATH=/bin:/sbin:/usr/bin:/usr/sbin:/usr/local/bin:/usr/local/sbin:~/bin
export PATH

read -p "Please input (Y/N): " yn

if [ "${yn}" == "Y" ] || [ "${yn}" == "y" ]; then
	echo "OK, continue"
	exit 0
fi
if [ "${yn}" == "N" ] || [ "${yn}" == "n" ]; then
	echo "Oh, interrupt!"
	exit 0
fi
echo "I don't know what your choice is" && exit 0
或者

#!/bin/bash
# Program:
#       This program shows the user's choice
# History:
# 2015/07/16    VBird   First release
PATH=/bin:/sbin:/usr/bin:/usr/sbin:/usr/local/bin:/usr/local/sbin:~/bin
export PATH

read -p "Please input (Y/N): " yn

if [ "${yn}" == "Y" ] || [ "${yn}" == "y" ]; then
	echo "OK, continue"
elif [ "${yn}" == "N" ] || [ "${yn}" == "n" ]; then
	echo "Oh, interrupt!"
else
	echo "I don't know what your choice is"
fi
可用test測試檔案的類型及權限判斷

test -f /home/user1/file1 (用echo $?取出結果)
test -f /home/user1/file1
if [ -r /home/user1/file1 ]; then
測試帳號是否存在

#!bin/bash
read -p "input account:" account
isexist=$(id"$account")  #將id執行結果存在isexsit中

if [ "$isexist" == "" ]; then
 echo "not exist" 
else
 echo "account exist!!"
fi
鳥哥，test : http://linux.vbird.org/linux_basic/0340bashshell-scripts.php#test
鳥哥，if/then : http://linux.vbird.org/linux_basic/0340bashshell-scripts.php#ifthen
宣告變數()

function

鳥哥 : http://linux.vbird.org/linux_basic/0340bashshell-scripts.php#function
工作排程
at
只會執行一次
-m 會寄email
範例:
at -m 3pm
at> echo hello
atrm 1 將job1刪除

atq 檢視還剩下哪幾個工作

crontab
會重複一直執行
執行 crontab -e
分 時 日 月 周 身份 指令
例如 0 9,11 * * * bash /home/user1/job1.sh 於每日9點及11點執行
例如 0 9-11 * * * bash /home/user1/job1.sh 於每日9點到11點執行
*/5 * * * * bash /home/user1/job1.sh 每5分鐘執行一次
鳥哥 : http://linux.vbird.org/linux_basic/0430cron.php
壓縮與備份
常見壓縮檔:
副檔名	說明
*.tar	以tar程式打包的檔案，未壓縮
*.tar.gz(*)	以tar程式打包檔案，並以gzip壓縮
*.tar.bz2	以tar程式打包檔案，並以bzip2壓縮
*.tar.xz	以tar程式打包檔案，並以xz壓縮
範例

壓縮後生成file1.xz，並刪除原始檔
xz file 
壓縮後生成file1.xz，並保留原始檔
xz -k file
解壓縮並刪除壓縮檔
xz -d file1.xz
tar 用於將多個檔案合併為一個檔案，以利備份和壓縮

將 dir1 下所有檔案合併到test.tar
tar -cf test.tar dir1
再用gzip產生test.tar.gz
gzip test.tar
選項	說明
-c	建立檔案
-x	解開檔案
-v	顯示過程
-t	查看內容
-f	被處理檔案名稱(一定要是最後一個參數)
-z	由gzip處理
-j	由bzip2處理
-J	由xz處理
-C	指定目的的路徑
tar 配合壓縮與解壓縮範例
把dir1打包然後壓縮成不同的壓縮檔格式
tar -zcf test.tar.gz dir1
tar -zcf test.tgz dir1 (tar.gz的縮寫)
tar -jcf test.tar.bz2 dir1
tar -Jcf test.tar.xz dir1
檢視壓縮檔內容物 tar -tvf test.tar.gz
解開tar壓縮檔
tar -zxf test.tar.gz
tar -zxf test.tgz    (縮寫)
tar -zxf test.tar.gz -C /tmp
tar -jxf test.tar.bz2
tar -Jxf test.tar.xz
帳號與群組管理
帳號及對應編號(UID)
UID	群組身分	帳號範例
0	root群組	root
1~9999	系統服務群組	cdrom、daemon
1000~65535	一般群組	user1(1000)、user2(1001)
群組及其對應編號(GID)
GID	群組身分	帳號範例
0	root群組	root
1~9999	系統服務群組	cdrom、daemon
1000~65535	一般群組	user1(1000)、user2(1001)
主要群組與次要群組

一個帳號只能有一個主要群駔
一個帳號可以同時擁有多個次要群組
帳號若沒有主要群組，則會無法登入
新增帳號時，預設會指定一個與帳號同名的主要群組
/etc/passwd : 每行代表一個帳號，以:分隔以下欄位 (預設任何人皆可檢視此檔案內容)

1. 使用者帳號
2. 密碼，顯示x表示已改存於/etc/shadow
3. 帳號UID
4. 帳號GID
5. 帳號備註
6. 家目錄路徑
7. 預設使用的shell

/etc/shadow : 每行代表一個帳號，以:分隔以下欄位 (預設只有root或者shadow群組的帳號才可以檢視)
1. 帳號名稱
2. 家密後的密碼
3. 密碼最後改變的日期
4. 密碼不可被更動的天數(指定兩次變更密碼最短必須間隔多少天)
5. 這組密碼還有多久會過期(最多只能使用幾天，然後就要更改密碼)
6. 警告更改密碼間隔天數(設定在密碼過期前幾天，對使用者提出警告訊息)
7. 密碼過期後還有多久會解除(設定當密碼過期後，讓使用者還有多少天可以登入更改密碼。如果密碼過期之後，又超過這麼久的時間沒有登入更改密碼，則密碼就會被停用，無法登入，這時候就要由系統管理者處理了。)
8. 帳號還有多久會過期(此數值是從 1970 年 1 月 1 日算起的天數，如果這個欄位是空的，就代表此帳號不會過期，可以一直使用。)
9. 保留欄位
/etc/group : 一行代表一個群組，以:分隔以下欄位 (預設任何人皆可檢視此檔案內容)
1. 群組名稱
2. 群組密碼，顯示x表示已改存於/etc/shadow
3. GID
4. 群組會員
/etc/gshadow : 以:分隔以下欄位 (預設只有root或者shadow群組的帳號才可以檢視)
1. 群組名稱
2. 家密後的群組密碼
3. 群組管理員帳號
4. 群組會員
su、sudo
切換帳號 su [帳號]
需輸入新帳號的密碼
預設切換成root
切換後會產生子shell
返回原帳號用exit
su root     (切換成root，但使用原帳號的環境變數設定與mail等等)
su - root   (切換成root，使用root的環境變數設定與mail等等)
exit
sudo [指令]
暫時使用root權限，執行完畢之後立即消失
需使用目前帳號的密碼
可利用sudo 執行updatedb更新檔案索引表
只有寫於 /etc/sudoers設定黨內的帳號才可以使用sudo
以root權限執行visudo
## Allow root to run any commands anywhere
root    ALL=(ALL)       ALL  #找到這行
user1   ALL=(ALL)       ALL  #加上這行使user1擁有使用sudo的權限
wheel 群組也可以使用sudo
## Allows people in group wheel to run all commands
%wheel  ALL=(ALL)       ALL   
執行 sudo usermod -G wheel user1 將user1次要群組設定為wheel
鳥哥: usermod
切換成root帳號也可以使用sudo -i 只需輸入原帳號的密碼(但是要再sudoer設定檔內)
新增修改移除帳號
更改密碼
以root權限更改密碼就不會有密碼提示太簡單的問題
passwd [帳號]
sudo passwd [帳號] (以root權限更改密碼)
echo user1:1234|sudo chpasswd  (適合用於自動化腳本)
新增帳號
useradd user3    #建立帳號後會自動建立同名群組
passwd user3     #建立密碼，若無建立密碼則無法登入
建立多筆帳號script範例(密碼皆為12345)
#!bin/bash
for((i=1;i<10;i++))
do
 echo "Adding student""$i"
 useradd student"$i"  #這邊建立帳號 
 echo student"$i":12345|chpasswd  #修改密碼
done
修改帳號
usermod [option] [username]
選項	說明
-u	設定新UID
-d	設定家目錄
-g	設定主要群組
-G	設定次要群組
-a	附加次要群組
-L	鎖定帳號(無法登入)
-U	解鎖帳號
移除帳號
userdel [帳號]
userdel -r -f user3 -f :強制移除帳號，-r: 刪除家目錄及其他檔案(例如信箱或工作排程)
新增修改移除群組(需root權限)
sudo groupadd group1           #新增group1
sudo groupadd -g 1004 group2   #新增group2 並設定gid為1004
sudo groupmod -g 1005          #修改group2 gid
sudo groupmod -n group3        #修改group2 名稱為group3
sudo group [groupname]         #刪除group (若仍有主要成員則無法刪除)
查詢帳號資訊
users :顯示目前登入的帳號，資訊較簡略

who :顯示目前登入的帳號，較詳細

w [帳號(可不加)] :只顯示目前入的指定帳號，資訊最完整

查詢帳號所屬群組

[root@localhost ~]# groups user1
user1 : user1
groups [帳號] 
輸出: [帳號]: [主要群組] [次要群主]
印出帳號群組相關資訊
[root@localhost ~]# id user1
uid=1000(user1) gid=1000(user1) groups=1000(user1),10(wheel)
列出每個帳號最近登入的時間
lastlog
顯示系統登入紀錄
last -n 3    #顯示最近3筆紀錄
last user1   #只顯示user1登入紀錄
last reboot  #顯示重開機紀錄
檔案管理權限
檢視檔案資訊
-rwxrwxrwx.  1 root root   176 Dec 28  2013 .bashrc
從左到右分別是檔案屬性、連結數、擁有者、群組、檔案大小，檔案最後存取日期，檔名

-rwxrwxrwx. :- 代表檔案類型(d為目錄，-為檔案)，前3個rwx為檔案擁有者屬性(可讀可寫可執行)，中間三個為檔按所屬群組之屬性，後三者為其他人對此檔案之屬性

只有主要群組為第四欄位群組才有權限，若無則為後三個權限 (權限判斷是依據主要群組判斷)

變更檔案權限 (-R:遞迴)

鳥哥chmod
鳥哥chown
鳥哥chgrp
前景及背景
執行中的程式按ctrl + z 暫停並丟到背景

輸入jobs 查看背景程序狀態

-l 列出jobnumber 指令與PID
-r 列出正在背景執行的程序
-s 列出正在背景暫停的程序
輸入ps 會同時看到背景及前景的狀態

使用 fg %n 將第n個程序切換到前景執行

使用 bg %n 讓第n個job(程序)於背景執行

使用kill [-信號] PID 終止程序

先查出PID(firefox): ps aux|grex firefox
編號	意義
-2	ctrl + c
-9	強制刪除process
-15(預設)	以正常程序通知程式停止
範例:
kill 12345
kill -9 12345
xkill 用滑鼠點擊視窗來刪除程序

ssh與防火牆設置
ping www.google.com 發送封包，測試連線

ping -c 3 www.google.com 只發送3次

nslookup [網址/ip] 用ip/主機 查詢 ip/主機(網址)

ssh:

有時候會出現connection refuse 這時候可以輸入以下指令查看
master@ubuntu:~/Desktop$ sudo service ssh restart
Failed to restart ssh.service: Unit ssh.service not found.
代表沒有安裝ssh (ubuntu預設不會安裝)
執行以下指令
sudo apt-get install ssh
防火牆

查看防火牆狀態
sudo ufw status
關閉防火牆
sudo ufw disable
開啟防火牆
sudo ufw enable
開啟port
sudo ufw allow 22/tcp   #開啟22port(ssh預設22port)
sudo ufw allow 80/tcp   或 sudo ufw allow http   #開啟80port(就是http)
sudo ufw allow 443/tcp  或 sudo ufw allow https  #開啟443port(就是https)
sudo ufw allow from 127.0.0.1 to any port 22   #只允許特定ip連接 22port(例如 127.0.0.1)
scp

出現permission denied
解決方法:
登入root
修改權限到777 (不安全)sudo chmod 777 /home
先scp到/tmp目錄 (一定可以，因為/tmp是用來放公共資料的地方)
