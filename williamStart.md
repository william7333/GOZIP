# 빌드 및 실행
docker compose up -d --build

# 상태 확인
docker compose ps

# backend가 실행된 뒤 DB 테이블 생성
docker compose exec backend python manage.py migrate

# 처음 구성한 DB에 데이터 넣기: scripts/ 경로가 필요합니다
docker compose --profile scripts run --rm scripts python scripts/03_import/import_all.py

# 중개사 신뢰도 데이터 처리
docker compose --profile scripts run --rm scripts python scripts/03_import/trust/import_trust_all.py