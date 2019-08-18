![서비스 모델]()
* 문제점
    * 많은 데이터가 들어오는데 데이터 업데이트가 너무 느림\
    * 데이터 fetching도 느림\
//////////\
장고 ORM 편하겠다\
//////////
* Silk
    * live benchmarking 가능
    * 여러개 한번에
    * 프로파일 그래프, 트레이스백
    * 응답 느려짐
    * ORM 안쓴 쿼리 안 보여줌
* 어떻게 고쳤나?
    * 빠르게 올리자
    * 환자 하나씩 저장해서 느리다
    * bulk_create : 이미 존재하는 row는 불가
    * delete_and_create : 일부 데이터만 받으면 기존 정보가 날라감
    * row 쿼리(ON DUPLICATE KEY UPDATE)
//////////\
어떻게 25배 차이가 나냐\
//////////\
    * 빠르게 가져오자
    * select_related
    * preferch_related : 쿼리가 두개지요
    * indexing : 자주 사용되는건 o 근데 속도 저하 유발 가능
    * batching : 한꺼번에 해서 빠름
