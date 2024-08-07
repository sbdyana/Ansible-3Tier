# Cloud Project : 3-Tier



### 개요

------

3-Tier Architecture 구현 및 검증



### 인프라

------

| IP               |   OS   | cpu/ram |       Name       | 용도                        |
| :--------------- | :----: | :-----: | :--------------: | --------------------------- |
| **77.88.140.11** | Ubuntu | 4/4/60  |    sb.yang-v1    | Ansible server<br />haproxy |
| **77.88.140.23** | Ubuntu | 2/4/16  | Slt_sb.yang_WEB1 | nginx                       |
| **77.88.140.24** | Ubuntu | 2/4/16  | Slt_sb.yang_WEB2 | nginx                       |
| **77.88.140.25** | Ubuntu | 2/4/16  | Slt_sb.yang_WAS1 | tomcat                      |
| **77.88.140.26** | Ubuntu | 2/4/16  | Slt_sb.yang_WAS2 | tomcat                      |
| **77.88.140.27** | Ubuntu | 2/4/30  | Slt_sb.yang_DB1  | mysql                       |
| **77.88.140.28** | Ubuntu | 2/4/30  | Slt_sb.yang_DB2  | mysql                       |



### 회차 별 요구사항

------

##### 2024/06 1회 차 

- Git을 통한 버전 관리
- 구성도 이미지
- 원하는 방식의 데이터 사용
- WEB / WAS / DB 구축

- 1회 차 Architecture
  ![1차Architecture](https://raw.githubusercontent.com/sibiniiii/my-images/main/img/1%E1%84%8E%E1%85%A1Architecture.png)

##### 2024/07 2회 차

- Git을 통한 버전 관리
- WEB / WAS / DB 이중화 구현
- 인증서 적용 
- 2회 차 Architecture
  ![2차Architecture](https://raw.githubusercontent.com/sibiniiii/my-images/main/img/2%E1%84%8E%E1%85%A1Architecture.png)

##### 2024/08 3회 차 

- 2차 과제 고도화

