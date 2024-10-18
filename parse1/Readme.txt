conda activate penv312

# 필요 라이브러리 설치
pip install psycopg2-binary sqlalchemy pandas scikit-learn flask
conda install psycopg2-binary sqlalchemy pandas scikit-learn flask


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