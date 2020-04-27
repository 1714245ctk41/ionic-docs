---
previousText: 'Runtime Errors'
previousUrl: '/docs/troubleshooting/runtime'
nextText: 'CORS Errors'
nextUrl: '/docs/troubleshooting/cors'
contributors:
  - FdezRomero
  - brandyscarney
---

# ネイティブエラー

## コードの署名エラー

```shell
Code Signing Error: Failed to create provisioning profile. The app ID "com.csform.ionic.yellow" cannot be registered to your development team. Change your bundle identifier to a unique string to try again. Code Signing Error: No profiles for 'com.csform.ionic.yellow' were found: Xcode couldn't find any iOS App Development provisioning profiles matching 'com.csform.ionic.yellow'. Code Signing Error: Code signing is required for product type 'Application' in SDK 'iOS 11.1'
```

iOSデバイスでアプリケーションを実行するには、プロビジョニングプロファイルが必要です。プロビジョニングプロファイルが作成されていない場合は、次の手順に従います:

1. <strong>[Package ID](/docs/reference/glossary#package-id) を設定する。</strong>

    Capacitor の場合、`capacitor.config.json` ファイルを開き `appId` プロパティを修正します。

    Cordova の場合、`config.xml` ファイルを開き、ルート要素 `<widget>` の `id` 属性を修正します。よりくわしい情報は [Cordova ドキュメント](https://cordova.apache.org/docs/ja/9.x/config_ref/index.html#%E3%82%B3%E3%82%A2%E6%A7%8B%E6%88%90%E8%A6%81%E7%B4%A0) をご参照ください。

2. <strong>プロジェクトを <b>Xcode</b> で開く。</strong>

    Capacitor の場合、以下を実行し Xcode でアプリケーションを開いてください:

    ```shell
    $ ionic capacitor open ios
    ```

    Cordova の場合、Xcode 開きます。**File** &raquo; **Open** からアプリケーションを見つけます。アプリケーション内の `platforms/ios` ディレクトリを開きます。

3. <strong><b>プロジェクト ナビゲーター</b>で、プロジェクトのルートを選択しエディタでプロジェクトを開きます。**Identyty** セクションで、設定された Package ID がバンドル識別子と一致することを確認します。</strong>

    ![Xcode Identity Setup](/docs/assets/img/running/ios-xcode-identity-setup.png)

4. <strong>同じプロジェクトエディタの <b>署名</b> セクションで、<b>Automatically manage signing</b> が有効になっていることを確認します。</strong> 次に、Team から開発チームを選択します。開発チームがあれば、Xcode はプロビジョニングと署名を自動的に準備しようとします。

    ![Xcode Signing Setup](/docs/assets/img/running/ios-xcode-signing-setup.png)


## Xcode のビルドエラー 65

```shell
Error: Error code 65 for command: xcodebuild with args: -xcconfig,/Users/ionitron/projects/my-project/platforms/ios/cordova/build-debug.xcconfig,-workspace,SC project.xcworkspace,-scheme,SC project,-configuration,Debug,-sdk,iphonesimulator,-destination,platform=iOS Simulator,name=iPhone X,build,CONFIGURATION_BUILD_DIR=/Users/ionitron/projects/my-project/platforms/ios/build/emulator,SHARED_PRECOMPS_DIR=/Users/ionitron/projects/my-project/platforms/ios/build/sharedpch
```

このエラーは Xcode のエラーコードで、プロビジョニングの問題または古いcordova依存関係が原因で発生する可能性があります。このエラーを修正するには、まず上記の手順でプロビジョニングプロファイルが生成されていることを確認したのち、[Xcode からアプリケーションを実行します](/docs/developing/ios#running-with-xcode)。

もしそれでもエラーが解決しない場合は、次のコマンドを実行してください:

```shell
rm -rf node_modules
rm -rf platform
npm i
ionic cordova platform add ios
ionic cordova prepare ios
ionic cordova build ios --prod
```

Once these commands have been ran a fresh build can be done.


## Google Play Servicesのバージョンが衝突

```shell
Error: more than one library with package name com.google.android.gms
```

このエラーは、2つの異なるプラグインが異なるバージョンの  `Google Play Services` を使用しようとしたことが原因です。この問題を解決するには、バージョンが `7.1.0` 以上の `cordova` および バージョンが `6.3.0` 以上の `cordova-android` を実行していることを確認してください。最新の `cordova` をインストールするには次を実行してください:

```shell
$ npm install cordova@latest
```

また、`cordova-android` をアップデートするには次を実行してください:

```shell
$ cordova platform update android
```


`Google Play Services` に依存するプラグインをアップデートして、同じバージョンを使用できるようになりました。例えば、`pluginA` ではバージョン 11.0 を使用し、`pluginB` では バージョン 15.0 を使用する場合、`config.xml` ファイルでは以下のスニペットで同じバージョンを使用するように更新できます:

```xml
<plugin name="pluginA" spec="npm">
  <variable name="PLAY_SERVICES_VERSION" value="15.0.0"/>
</plugin>
<plugin name="pluginB" spec="npm">
  <variable name="PLAY_SERVICES_VERSION" value="15.0.0" />
</plugin>
```
