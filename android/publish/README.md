



## Gotcha

### play store の version code の制約

- version code は常にインクリメントしないといけない
- するトラックに既に aab/apk が up されている場合, 次にupするものはそれらのバージョンコードより大きいバージョンコードを持たないといけない.


### play store からアプリを削除する場合の影響

#### 再度同じ package 名のアプリをアップロード

- firebase app distribution の再設定
  -  https://console.firebase.google.com/project/YOUR_PROJECT_NAME/settings/integrations/playlink から app を play store にリンクしなおす


