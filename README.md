# 부산영업팀 화주분석

ERP 부킹 리스트 엑셀(.xls/.xlsx)을 브라우저에서 불러와 화주·포워더·영업사원·부킹을 분석하는 페이지입니다.
데이터는 들어 있지 않고, 사용자가 고른 엑셀을 **브라우저 안에서만** 읽습니다. 서버로 전송하거나 저장하지 않습니다.

## 구성
- `index.html` : 화면 전체
- `vendor/xlsx.full.min.js` : 엑셀 읽기 라이브러리 (SheetJS 0.18.5, 인터넷 없이도 동작)
- `.gitignore` : 엑셀·CSV 파일이 저장소에 올라가지 않도록 막음

## 사용
1. 페이지 접속
2. 오른쪽 위 **엑셀 불러오기** 또는 파일을 화면에 끌어다 놓기
3. 다른 달 자료는 새 파일을 다시 불러오면 바로 바뀝니다

필요한 열: B/K No, Org Shipper, Shipper, SALESNM, C20, C40, C45, TEU, SVC, VSL, VOY, ETD, POD, DAREA, FE, SOC, B/K Type

## 계산 기준
- 화주 = Org Shipper, 포워더 = Shipper
- 40ft = C40 + C45(40HC), TEU = 파일의 TEU 값
- 구분: FE가 EMPTY면 EMPTY, SOC 열이 SOC/Y 또는 B/K Type이 LINE SOC면 SOC, 나머지는 COC
- 기본 화면은 EMPTY 제외(COC+SOC)
- 월은 ETD 기준

## 주의
엑셀 파일을 저장소에 커밋하지 마세요. 공개 저장소에 올라가면 화주 정보가 외부에 노출됩니다.
