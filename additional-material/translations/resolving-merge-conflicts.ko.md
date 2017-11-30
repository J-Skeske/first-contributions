# 병합 충돌이 무엇인가요?

여러분이 또 다른 브랜치에서 현재 작업중인 브랜치로 병합하고자할 때, 또 다른 변경사항들도 같이 반영되어야 하므로 여러분의 현재 작업중인 파일들에 같이 결합이 이루어지게 됩니다.
만일 이때 두 사람이 같은 파일의 똑 같은 라인을 (각자 다르게)변경했거나 다른 사람이 수정 반영한 곳을 삭제하려고 한다면 Git은 어느 변경사항이 옳은 것인지 쉽게 판단할 수 없습니다. 
이때 Git은 여러분 스스로 이 문제를 반드시 해결하도록 충돌이 있음을 파일에 표시합니다.


# 병합 충돌은 어떻게 해결하나요?

병합 충돌이 발생하면 Git은 문제가 되는 부분에 “<<<<<<<< HEAD” 와 “>>>>>>>>>>[other branch name]” 으로 감싸서 표시합니다.

이때 여러분이 현재 작업중인 브랜치가 먼저 표기됩니다. 꺽쇠기호 뒤를 보면 어느 브랜치에서 변경사항이 반영되었는지 알 수 있습니다.
"=======" 기호는 충돌이 발생한 부분을 각각 구분해줍니다.
여러분이 해야할 일은 바로 위와 같은 충돌표시들을 원하는 코드만 보이도록 깨끗하게 정리하는 것입니다.
따라서 충돌을 발생케한 여러분의 동료와 어느 변경사항이 옳은 것인지 서로 이야기를 나눠야합니다.
여러분의 변경사항이 옳을 수도 있고 그렇지 않을 수도 있습니다. 아니면 양자 모두의 변경사항을 합쳐야만 하는 경우도 있을 수 있겠죠.


예시: 
```
 <<<<<<< HEAD:mergetest
 This is my third line
 =======
 This is a fourth line I am adding
 >>>>>>> 4e2b407f501b68f8588aa645acafffa0224b9b78:mergetest
```

<<<<<<<: 병합 충돌이 시작되는 곳을 표시합니다. 여러분이 병합하고자하는 변경한 라인들로 이루어진 부분이 첫번째로 표기됩니다.
=======: 비교하기 위한 구분선을 나타냅니다. 쉽게 차이를 파악할 수 있도록 사용자가 커밋한 변경사항(위)과 병합을 위해 로드된 부분(아래)으로 구분되어 있습니다. 
>>>>>>>: 병합 충돌이 발생한 마지막 위치를 표시합니다.


Git에서 병합하는 것에 문제가 있는 부분을 일일이 수작업으로 편집해서 병합하면서 충돌문제를 해결합니다.
이는 여러분의 수정사항을 삭제하거나 다른 누군가의 변경사항을 지우는 일이며 또는 이 두 부분을 하나로 합치는 것을 의미합니다.
그리고 해당 파일에서 '<<<<<<<', '=======', 그리고 '>>>>>>>'을 지워야합니다.

일단 충돌을 해결했다면 `git add`를 실행합니다. 
아울러 충돌이 올바르게 해결되었는지 확인하기 위해 반드시 테스트를 수행하는 것을 잊지마십시요.

병합 충돌을 보다 쉽게 해결하려면 여러분이 사용하는 각각의 IDE에 맞는 적절한 플러그인을 다운로드 받아 설치하세요.

# 병합을 어떻게 되돌리나요?
병합을 취소하려면 `git merge —abort` 명령을 실행하세요.