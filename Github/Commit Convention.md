# Commit Convention

회사에서 팀 단위로 개발을 진행하다보니 Git Commit Convention의 중요성을 느꼈습니다.

커밋 메시지: 제목, 선택적인 본문 및 바닥글로 구분 됩니다.

```
Type: Subject

Body

Footer
```

```
TYPE / JIRA ∂l슈 번호 - 설명

[본문 - 선택사항]

[꼬리말 - 선택사항]
```

## Type

- **feat:** A new feature | [새로운 기능 추가]
- **fix:** A bug fix | [버그 수정]
- !**hotfix:** 급하게 치명적인 버그 고쳐야 하는 경우 🚨
- **docs:** Changes to documentation | [문서수정]
- **style:** Formatting, missing semi colons, etc; no code change
  - 포맷, 세미콜론 수정, Optimize import, Code clean up 등 코드가 아닌 코드 스타일 관련된 수정]
    
- **refactor:** Refactoring production code | [리펙토링]
- **test:** Adding tests, refactoring test; no production code change | [테스트 코드 추가]
- **chore:** Updating build tasks, package manager configs, etc; no production code change
  - 빌드 업무 수정, 패키지 매니저 수정
    
- **design:** 퍼블리싱

### ADD…

- **Remove**: 코드의 삭제가 있을 때 사용합니다. ‘Clean’을 사용하기도 합니다.
- **RENAME:** 이름 변경이 있을 때 사용합니다.
- **UPDATE:** 개정이나 버전 업데이트가 있을 때 사용합니다. (코드보다는 문서나 리소스, 라이브러리에 사용)

## Subject

제목은 50자를 넘기지 않고 대문자로 시작하여 서술어가 아닌 명사로 끝나야 하고, 마침표는 사용하지 않습니다.

## Body

본문 내용은 선택사항 입니다. 72자를 넘기지 않고 제목과 한줄 띄워서 작성합니다. 

무엇을, 왜 변경하였는지 기술하는게 목적입니다.

## Footer

이슈 트랙킹을 위해 ID를 참조하는데 사용합니다.
