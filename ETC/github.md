## 깃허브?   
Git: 분산형 버전 관리 시스템(Version Control System)  
Git을 활용할 수 있게 돕는 사이트 중 하나이다.
<br/>

***구조: 스테이지 -> 로컬 저장소 -> 원격 저장소***  

과정은 아래와 같다.  
```
   -> ***Staging Area***   
git init(깃 저장소를 초기화 후, history가 저장되는 .git 폴더 생성, 저장소 내에서 파일을 add 가능한 상태가 됨)  
git add 파일명(깃이 주변 모든 파일을 지켜봄 = tracking, staged 상태로 만듦) 
git status(저장소 상태 확인)   
git rm 파일명(로컬, 원격저장소에서 파일 삭제) 
git rm --cached 파일명(로컬 저장소에는 남겨놓되 commit시 원격저장소에서 파일 삭제) -> .gitignore 파일로 제외하는 게 편함

   -> ***Local Repository***  
git commit -m "메모할 내용"(특정 시점에서 변경된 정보를 기록하여 로컬 저장소에 저장함)
git log(커밋 기록 확인)    
   -> ***Remote Repository***     
git push -u origin master(로컬 저장소master의 내용을 원격 저장소origin로 저장)  
origin: 원격주소, master: 브랜치  
                        
로컬 저장소 <- 원격 저장소   
git clone(원격저장소를 복사해 붙여넣음 즉, 기존 로컬 파일을 덮어 죽여버리니 초기에만 실행)  
git fetch(원격저장소 최신 메타데이터 확인)  
git pull(원격저장소 최신 메타데이터 확인fetch + 병합merge)  
git fork(다른 프로젝트 저장소 불러옴)  
```
## 기억해야 할 단어  

Repository: 여러 파일, 소스코드와 더불어 커밋 내역까지 담긴 저장소  

Snapshot: 특정 시점에서의 파일 상태     

Head: 현재 작업중인 Branch  

Master: 처음 시작했을 때 생성된 분기  

Branch: 현 시점의 저장소를 복사하여 만든 새로운 분기  

Merge: 작업이 완료된 다른 Branch를 현재 Branch에 합침  

Checkout: 이전 분기들 중 하나로 되돌림  
