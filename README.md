# document
「病人資料」  
pid 病歷號  
pname 病人姓名  
birthday 病人生日 (如2019-01-01)   
sex 病人性別  (如M、F、O)   
telephone 病人電話  
address 病人住址  
  
「檢查單」
seq 工單號  
patientid　病歷號  
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
  
  
  
「病人資料」  
BEGIN;  
-- CREATE TABLE "patient" -------------------------------------  
CREATE TABLE "public"."patient" (  
	"id" Integer DEFAULT nextval('patients_id_seq'::regclass) NOT NULL,  
	"pid" Character Varying( 20 ),  
	"pname" Character Varying,  
	"birthday" Date,  
	"sex" Character Varying( 2 ),  
	"telephone" Character Varying( 20 ),  
	"address" Text,  
	"flag" Integer,  
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
	"id" Integer DEFAULT nextval('examines_id_seq'::regclass) NOT NULL,  
	"seq" Character Varying( 20 ),  
	"eseq" Character Varying( 20 ),  
	"typeid" Character Varying( 5 ),  
	"typename" Character Varying,  
	"source" Character Varying( 5 ),  
	"stat" Integer,  
	"statname" Character Varying,  
	"chargdate" Date,  
	"chargtime" Time Without Time Zone,  
	"logindate" Date,  
	"logintime" Time Without Time Zone,  
	"orderdr" Character Varying( 10 ),  
	"orderdrname" Character Varying,  
	"studydr" Character Varying( 10 ),  
	"studydrname" Character Varying,  
	"enterdr" Character Varying( 10 ),  
	"enterdrname" Character Varying,  
	"orderdate" Date,  
	"ordertime" Time Without Time Zone,  
	"completedate" Date,  
	"completetime" Time Without Time Zone,  
	"enterdate" Date,  
	"entertime" Time Without Time Zone,  
	"report" Text,  
	"pacsno" Numeric,  
	"flag" Integer,  
	"created_at" Timestamp Without Time Zone NOT NULL,  
	"updated_at" Timestamp Without Time Zone NOT NULL,  
	"worksense_id" Integer,  
	"scopy_id" Integer,  
	"patient_id" Integer,  
	PRIMARY KEY ( "id" ) );  
 ;  
-- -------------------------------------------------------------  
  
-- CREATE INDEX "index_examines_on_workbook_id" ----------------  
CREATE INDEX "index_examines_on_workbook_id" ON "public"."examines" USING btree( "worksense_id" Asc NULLS Last );  
-- -------------------------------------------------------------  
  
COMMIT;  

