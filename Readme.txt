

## 파일구성 

>
model-make 
    - 모델을 훈련 및 모델을 생성
model-analysys.ipynb
    - 파라메타로 넘어온 데이타를 모델을 기반으로 이상여부 분석 후 결과 리턴
dashboard-newdata.ipynb
    - 데이타베이스에서 신규 데이타를 주기적으로 확인하여 이상여부 분석 의뢰 및 이상으로 탐지 될 경우 탐지 데이타 저장
dashboard-user2.ipynb
    - 사용자별 이벤트 수와 이상탐지 통계 대시보드 샘플


## parse1 참고


## 실행 준비
conda activate penv312

### 필요 라이브러리 설치
pip install psycopg2-binary sqlalchemy pandas scikit-learn flask requests
conda install psycopg2-binary sqlalchemy pandas scikit-learn flask requests

conda activate penv312



### 데이타베이스 테이블 생성
-- public.anomaly_logs definition

-- Drop table

-- DROP TABLE public.anomaly_logs;

CREATE TABLE public.anomaly_logs (
	id serial4 NOT NULL,
	user_id varchar(50) NULL,
	document_id varchar(50) NULL,
	activity_type varchar(20) NULL,
	"timestamp" timestamp NULL,
	ip_address varchar(50) NULL,
	is_anomaly bool DEFAULT true NULL,
	anomaly_detected_at timestamp DEFAULT CURRENT_TIMESTAMP NULL,
	CONSTRAINT anomaly_logs_pkey PRIMARY KEY (id)
);


-- public.document_logs definition

-- Drop table

-- DROP TABLE public.document_logs;

CREATE TABLE public.document_logs (
	id serial4 NOT NULL,
	user_id varchar(50) NULL,
	document_id varchar(50) NULL,
	activity_type varchar(20) NULL,
	"timestamp" timestamp NULL,
	ip_address varchar(50) NULL,
	is_anomaly bool DEFAULT false NULL,
	CONSTRAINT document_logs_pkey PRIMARY KEY (id)
);