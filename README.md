# document
「病人資料」
BEGIN;

-- CREATE TABLE "patients" -------------------------------------

CREATE TABLE "public"."patients" ( 
	"id" Integer DEFAULT nextval('patients_id_seq'::regclass) NOT NULL,
	"pid" Character Varying,
	"pname" Character Varying,
	"birthday" Date,
	"sex" Character Varying,
	"telephone" Character Varying,
	"address" Character Varying,
	"created_at" Timestamp Without Time Zone NOT NULL,
	"updated_at" Timestamp Without Time Zone NOT NULL,
	PRIMARY KEY ( "id" ) );
 ;
-- -------------------------------------------------------------

COMMIT;



「檢查單」
BEGIN;
-- CREATE TABLE "examines" -------------------------------------
CREATE TABLE "public"."examines" ( 
	"id" Integer DEFAULT nextval('examines_id_seq'::regclass) NOT NULL,
	"seq" Character Varying,
	"eseq" Character Varying,
	"typeid" Character Varying,
	"typename" Character Varying,
	"source" Character Varying,
	"stat" Integer,
	"statname" Character Varying,
	"chargdate" Date,
	"chargtime" Time Without Time Zone,
	"logindate" Date,
	"logintime" Time Without Time Zone,
	"orderdr" Character Varying,
	"orderdrname" Character Varying,
	"studydr" Character Varying,
	"studydrname" Character Varying,
	"enterdr" Character Varying,
	"enterdrname" Character Varying,
	"orderdate" Date,
	"ordertime" Time Without Time Zone,
	"completedate" Date,
	"completetime" Time Without Time Zone,
	"enterdate" Date,
	"entertime" Time Without Time Zone,
	"report" Character Varying,
	"pacsno" Character Varying,
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

