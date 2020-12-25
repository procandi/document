# document

病人基本資料
URL：{Base URL}/patient/{Field}/{Data}

Method：GET only.

Form Data：
	{Base URL}目前為192.168.0.201，請在院內使用
	{Field}為cid則代表要比對身份證字號
	{Field}為tel則代表要比對電話號碼
	{Data}為Request data

Response JSON：
	id: Database Field ID
	pid: Patient ID
	pname: Patient Name
	birthday: Birthday
	sex: Sex
	telephone: Telephone
	address: Address
	cid: 身份證字號
	tag: 備註
	checkintime: 報到時間
	created_at: 資料建立時間
	updated_at: 最後一次更新資料時間


Sample:
http://192.168.0.201/patient/cid/S100454326
http://192.168.0.201/patient/tel/0953577227

{"id":425559,"pid":"00209782","pname":"吳金城","birthday":"1954-12-05","sex":"男","telephone":"0953577227","address":"台中市霧峰區中正路1196之2號4樓","created_at":"2020-03-31T11:13:16.000+08:00","updated_at":"2020-11-08T05:22:59.080+08:00","checkintime":null,"cid":"S100454326","tag":"123"}

Response null if target data is not available.