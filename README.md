# Cloud Project : 3-Tier



### 개요

3-Tier Architecture 구현 및 검증



------



### 인프라

| IP               |   OS   | cpu/ram |       Name       | 용도                        |
| :--------------- | :----: | :-----: | :--------------: | --------------------------- |
| **77.88.140.11** | Ubuntu | 4/4/60  |    sb.yang-v1    | Ansible server<br />haproxy |
| **77.88.140.23** | Ubuntu | 2/4/16  | Slt_sb.yang_WEB1 | nginx                       |
| **77.88.140.24** | Ubuntu | 2/4/16  | Slt_sb.yang_WEB2 | nginx                       |
| **77.88.140.25** | Ubuntu | 2/4/16  | Slt_sb.yang_WAS1 | tomcat                      |
| **77.88.140.26** | Ubuntu | 2/4/16  | Slt_sb.yang_WAS2 | tomcat                      |
| **77.88.140.27** | Ubuntu | 2/4/30  | Slt_sb.yang_DB1  | mysql                       |
| **77.88.140.28** | Ubuntu | 2/4/30  | Slt_sb.yang_DB2  | mysql                       |



------



### 회차 별 요구사항

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



------



### YAML

###### [haproxy]

- haproxy install

- haproxy.cfg.j2 copy

  - haproxy 도메인 ssl 인증서 적용 완료

  - haproxy를 통해 web1,2(nginx web) roundrobin(ssl verify 옵션 적용)

- ssl 적용을 위한 pem(root, service ca).j2 copy
- ssl verify를 위한 root 인증서 copy
- restart

###### [nginx]

- nginx install
- /etc/ssl에 인증서 cert copy
- openpage.html.j2 copy
- nginx.conf.j2 copy
  - was group 설정
  - 443 web ssl 적용
  - 8443 ssl 적용 > proxy_pass was 적용 완료
  - 80 > 443 redirect 적용(변수)
- enable, restart

###### [tomcat]

- /etc/ssl에 인증서 cert copy
- tomcat user, group 생성
- java install
- tomcat download (version 10.0.7)
- service.j2 copy (---)
- web.xml.j2 copy
  - welcome file 적용
- jsp.j2 copy
- mysql connector jar copy
- tomcat/conf에 cert.jks copy
- https block insert to server.xml(jks 필요) 
- Daemon reload, service start

###### [mysql]

- db.yml
  - mysql, dependencies install
  - enable, start
  - ssl 설정을 위한 cert copy
  - mysql user create
  - db database create
  - mysqld.cnf에 bind-address 설정

- db2.yml
  - mysqld.cnf에 master, slave 설정
- db3.yml
  - master - slave 연동
  - slave restart

