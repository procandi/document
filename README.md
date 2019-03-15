# document
「病人資料patient」  
id 病人流水號(不用寫)
pid 病歷號  
pname 病人姓名  
birthday 病人生日 (如2019-01-01)   
sex 病人性別  (如M、F、O)   
telephone 病人電話  
address 病人住址  
flag 交換註記 0 - 初次寫入， 1 - 資料已取走， 2 - 資料有更新  
  
「檢查資料examine」
id 檢查流水號(不用寫)
seq 工單號  
typeid　檢查類別ID (如GA)  
typename 檢查類別中文 (如內視鏡檢查)    
source 來源 (如門診、急診、住院)  
orderdr 開單醫師代碼  
ordername 開單醫師姓名  
orderdate 開單日期 (如2019-01-01)   
ordertime 開單時間 (如08:08:08)   
studydr 檢查醫師代碼  
studydrname 檢查醫師姓名  
studydate 檢查日期 (如2019-01-01)   
studytime 檢查時間 (如08:08:08)   
enterdr 報告醫師代碼  
enterdrname 報告醫師姓名  
enterdate 報告日期 (如2019-01-01)    
entertime 報告時間 (如08:08:08)    
report 報告內容  
flag 交換註記 0 - 初次寫入， 1 - 資料已取走， 2 - 資料有更新   
patient_id 病人流水號(對應patient.id)
  
  
「病人資料」  
BEGIN;  
-- CREATE TABLE "patient" -------------------------------------  
CREATE TABLE "public"."patient" (  
	"id" Integer DEFAULT nextval('patients_id_seq'::regclass) NOT NULL, 病人流水號(關聯鍵值)  
	"pid" Character Varying( 20 ), 病歷號  
	"pname" Character Varying, 病人姓名  
	"birthday" Date, 病人生日  
	"sex" Character Varying( 2 ), 病人性別  
	"telephone" Character Varying( 20 ), 病人電話   
	"address" Text, 病人住址  
	"flag" Integer, 交換註記 0 - 初次寫入， 1 - 資料已取走， 2 - 資料有更新  
	"created_at" Timestamp Without Time Zone NOT NULL,  
	"updated_at" Timestamp Without Time Zone NOT NULL,  
	PRIMARY KEY ( "id" ) );  
 ;  
-- -------------------------------------------------------------  
COMMIT;  



「檢查單」  
BEGIN;  
-- CREATE TABLE "examine" -------------------------------------  
CREATE TABLE "public"."examine" (  
	"id" Integer DEFAULT nextval('examines_id_seq'::regclass) NOT NULL,  檢查流水號(關聯鍵值)
	"seq" Character Varying( 20 ), 工單號  
	"eseq" Character Varying( 20 ), 工單號二  
	"typeid" Character Varying( 10 ), 檢查類別ID  
	"typename" Character Varying, 檢查類別中文  
	"source" Character Varying( 5 ), 來源  
	"stat" Integer, 檢查狀態  
	"statname" Character Varying, 開單醫師代碼  
	"chargdate" Date, 收費日期  
	"chargtime" Time Without Time Zone, 收費時間  
	"logindate" Date, 報到日期  
	"logintime" Time Without Time Zone, 報到時間  
	"orderdr" Character Varying( 10 ), 開單醫師代碼  
	"orderdrname" Character Varying, 開單醫師姓名  
	"studydr" Character Varying( 10 ), 檢查醫師代碼  
	"studydrname" Character Varying, 檢查醫師姓名  
	"enterdr" Character Varying( 10 ), 報告醫師代碼  
	"enterdrname" Character Varying, 報告醫師時間  
	"orderdate" Date, 開單日期  
	"ordertime" Time Without Time Zone, 開單時間  
	"studydate" Date, 檢查日期  
	"studytime" Time Without Time Zone, 檢查時間  
	"completedate" Date, 完成日期  
	"completetime" Time Without Time Zone, 完成時間  
	"enterdate" Date, 報告日期  
	"entertime" Time Without Time Zone, 報告時間  
	"report" Text, 報告  
	"pacsno" Character Varying( 20 ), pacs代碼  
	"flag" Integer, 交換註記 0 - 初次寫入， 1 - 資料已取走， 2 - 資料有更新  
	"created_at" Timestamp Without Time Zone NOT NULL,  
	"updated_at" Timestamp Without Time Zone NOT NULL,  
	"worksense_id" Integer, 感控流水號(關聯鍵值)  
	"scopy_id" Integer, 內視鏡流水號(關聯鍵值)  
	"patient_id" Integer, 病人流水號(關聯鍵值)  
	PRIMARY KEY ( "id" ) );  
 ;  
-- -------------------------------------------------------------  
  
COMMIT;  

