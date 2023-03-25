## 깃허브?   
Git: 분산형 버전 관리 시스템(Version Control System)  
Git을 활용할 수 있게 돕는 사이트 중 하나이다.
<br/>

***구조: Staging Area -> Local Repository -> Remote Repository***  

한 장으로 요약된 과정은 아래와 같다.  
```
   -> Staging Area    
git init(깃 저장소 초기화 + history가 저장되는 .git 생성 = 저장소 내 파일이 add 가능한 상태)  
git add 특정 파일명 또는 . (깃이 파일을 지켜봄 = 추적하여tracking 무대에 올림staged)   
git status(저장소 상태 확인)   
git rm 파일명 또는 . (로컬 파일 삭제 + add 후 commint, push하면 원격저장소 파일 삭제)  
git rm --cached 파일명(로컬 파일 그대로 두고 commit, push하면 원격저장소 파일 삭제)  
평소에는 .gitignore 파일로 그룹으로 묶어 제외하는 방법이 편리  
그러나 ***잘못 add한 경우 staging 영역에서 삭제하고자 git rm을 사용***  

   Staging Area -> Local Repository    
git commit -m "메모할 내용"(특정 시점에서 변경된 정보를 기록하여 로컬 저장소에 저장함)
git log(커밋 기록 확인)  

   Local Repository -> Remote Repository       
git push -u origin master(로컬 저장소master의 내용을 원격 저장소origin로 저장)  
origin: 원격주소, master: 브랜치  
                        
   Local Repository <- Remote Repository        
git clone(원격저장소를 복사해 붙여넣음 즉, 기존 로컬 파일을 덮어 죽여버리니 초기에만 실행)  
git fetch(원격저장소 최신 메타데이터 확인)  
git pull(원격저장소 최신 메타데이터 확인fetch + 병합merge)  
***원격저장소에 수정사항이 생겨 푸시가 안될 경우 pull을 사용***
git fork(다른 프로젝트 저장소 불러옴)  
```
수정사항 생기면 stage에서 내려오므로
tracking되고 있지만 staged되지 않은 파일을 staged 상태로 만들기 위해 git add(tracking + staged)
초록 글씨/붉은 글씨: staged 여부  
modified, unmodified: 수정사항 여부      

## 기억해야 할 단어  

Repository: 여러 파일, 소스코드와 더불어 커밋 내역까지 담긴 저장소  

Snapshot: 특정 시점에서의 파일 상태     

Head: 현재 작업중인 Branch  

Master: 처음 시작했을 때 생성된 분기  

Branch: 현 시점의 저장소를 복사하여 만든 새로운 분기  

Merge: 작업이 완료된 다른 Branch를 현재 Branch에 합침  

Checkout: 이전 분기들 중 하나로 되돌림  
