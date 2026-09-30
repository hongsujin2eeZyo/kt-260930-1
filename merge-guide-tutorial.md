# Git 병합 따라하기

## 병합이란?

병합은 한 브랜치에서 만든 커밋을 다른 브랜치의 이력에 합치는 작업입니다. 보통 작업 브랜치의 변경 사항을 `master`에 반영할 때 사용합니다.

## 단계별 예시

### 1. 작업 브랜치 만들기

```powershell
git switch master
git switch -c feature/login
```

### 2. 작업하고 커밋하기

파일을 수정한 뒤 변경 사항을 저장합니다.

```powershell
git add .
git commit -m "feat: add login"
```

### 3. 기본 브랜치로 이동하기

```powershell
git switch master
```

### 4. 작업 브랜치 병합하기

```powershell
git merge feature/login
```

## Fast-forward 병합

기본 브랜치에 새로운 커밋이 없고 작업 브랜치가 그 위에 곧바로 이어진다면 Git은 포인터만 앞으로 이동합니다. 이 방식이 fast-forward 병합입니다.

```powershell
git merge --ff-only feature/login
```

`--ff-only`는 fast-forward가 가능한 경우에만 병합하도록 하므로, 예상하지 못한 병합 커밋 생성을 막을 수 있습니다.

## 충돌이 발생하면

두 브랜치가 같은 부분을 다르게 수정하면 충돌이 발생할 수 있습니다. 충돌 표시를 직접 정리한 다음 다음 순서로 마무리합니다.

```powershell
git add <해결한-파일>
git commit
```

병합을 취소하려면 다음 명령을 사용합니다.

```powershell
git merge --abort
```