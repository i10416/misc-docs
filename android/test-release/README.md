## android の内部テストについて

### 内部トラックの分類
||internal test|internal app sharing|firebase app distribution|deploy gate|
|---|---|---|---|---|
play console へのアクセス|要|要|不要?|不要|
play store への初回リリース|要|要|不要|不要|
|既存のアプリとの共存( テスト版⇄本番のアプデなど)|不可能. internal test バージョンをアンインストールする必要がある|不可能. internal test バージョンをアンインストールする必要がある|不可能. internal test バージョンをアンインストールする必要がある|???|
|署名|アップロード鍵とplay storeのapp signing|__内部アプリ共有目的の証明書を利用できる__|アップロード鍵とplay store(app distribution)のapp signing|署名ずみapkをupする|
|build type|release|__debug&release__|release|release|
| アップロード・インストール形式|apk, aab|apk, aab| apk, aab | __apk__|
|共有方法|リンク・メーリングリスト→ playstore|リンク・メーリングリスト・google group→playstore|リンク・メーリングリスト -> app tester|リンク・メール|
|unique|beta環境、本番環境に　promoteできる|ユーザーがアプリをインストールするには端末の開発者モードを有効化する必要がある. build type, 署名, version code, permission　は任意の値. store listing 情報などがなくてもupできる. In App Reviewなどの機能が使える.||
|備考|初回リリース後、内部テストが完了してリリースを準備するために利用する. 問題なければbeta トラックにpromoteする. internal トラックは内部テスターに公開される. beta トラック以降は一般公開される.|初回リリース後、テスターに配布する前に __開発者__ がアプリをテストするために使う. 内部テスターに公開される.|リリース前にアプリ(特にaab)をテストするために使う|apkのテストに使う|


　参考
- https://speakerdeck.com/syarihu/internal-app-sharing-wan-quan-nili-jie-sita
- https://stackoverflow.com/questions/69140615/when-to-use-internal-app-sharing-vs-internal-testing-google-play

### firebase app distribution を利用したアプリの配布

https://console.firebase.google.com/project/__YOUR_PROJECT_NAME__/settings/integrations/playlink

から、firebase のプロジェクトとplay console を連携する必要がある.

また、内部テスト向けにupしたaabの審査を待つ必要がある.

