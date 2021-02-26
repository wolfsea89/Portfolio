Budowanie kontenera
=========

![Infrastructure](../images/dockerBuild.png)


### Omówienie joba
Po uruchomieniu joba, jenkins pobiera niezbędne repozytoria takie jak:
  - [Repozytorium Jenkinsfile](git@github.com:wolfsea89/Jenkins-Ci-Jenkinsfiles.git)
  - [Repozytorium Shared Library](git@github.com:wolfsea89/Jenkins-Sharedlibraries.git)
  - Kod aplikacji

Na podstawie jenkinsfile i Shared Library wykonywane są następujące zadania dla poszczególnych branchy:

branche: feature/*, epicfeature/*, develop

![Pipeline Release](../images/dockerJenkinsFileSnapshot.png)


branche: release/*, hotfix/*

![Pipeline Release](../images/dockerJenkinsFileRelease.png)

### Job steps
1. Pobieranie Repoyzotorium Shared Library
2. Zbieranie faktów
3. Pobieranie repozytorium JenkinsFile
4. Pobieranie repozytorium z kodem aplikacji
5. Uzuepłanianie faktów o jsona z instrukcjami dotyczącymi budowania i publikowania kontenera
6. Budowanie docker image
7. Publikowanie docker images
8. Sprzątanie (usuwanie obrazów)