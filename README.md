# stock_service


![image](https://github.com/user-attachments/assets/97e87dab-efbd-4fa0-b385-32ba8494a95b)

## 주요 기능
- **주식 정보 조회**: 주식 목록과 개별 주식 데이터를 조회
- **기술적 지표 계산**: SMA, 볼린저 밴드, MACD, RSI 등 계산
- **데이터 캐싱**: Redis를 사용하여 빈번히 조회되는 데이터 캐싱

<!--### 설계 개요 및 이유-->
### 모듈화된 서비스 계층
- **역할 분담**: 주식 데이터 조회와 변환 로직, 기술적 지표 계산 및 캐싱 로직 분리
- **유지보수성**: 코드의 가독성과 유지보수성 향상

### 캐싱 전략
- **성능 최적화**: Redis 사용으로 데이터베이스 조회 횟수 감소
- **효율적인 데이터 관리**: @Cacheable 어노테이션으로 캐싱 설정, 기술적 지표 계산 결과 캐싱

### 기술적 지표 계산
- **별도의 메서드로 분리**: 각 기술적 지표(SMA, 볼린저 밴드, MACD, RSI)를 별도의 메서드로 분리
- **캐싱을 통한 최적화**: Redis에 기술적 지표 계산 결과 저장

### 예외 처리 및 Kafka 통합
- **예외 처리**:
  - 주식 조회 예외
  - Redis 연결 문제 예외
  - 기술적 지표 계산 중 발생할 수 있는 예외
- **Kafka를 통한 에러 로깅**: 중앙화된 로그 시스템으로 에러 정보 전송, 실시간 모니터링 및 대응
