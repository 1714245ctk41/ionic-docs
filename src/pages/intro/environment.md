---
previousText: 'Overview'
previousUrl: '/docs'
nextText: 'CLI Installation'
nextUrl: '/docs/intro/cli'
contributors:
  - rtpHarry
---

# 環境設定

Ionic Frameworkをはじめるためには、[Node と npm](#anchor-node-npm)がインストールされている環境が必要です。

もちろん、エディタも必要でしょう。[Visual Studio Code](https://code.visualstudio.com/) をおすすめします。[Visual Studio Codeは無料で、 batteries-included text editor made by Microsoft.

## ターミナル

> Ionic開発の多くは、コマンドラインを利用する必要があります。コマンドラインに慣れていない場合は、[このブログ](https://ionicframework.com/blog/new-to-the-command-line/)で簡単な概要を確認してください。

一般的に、OSに最初からついているターミナルの使用をお勧めします。多くのサードパーティ端末はIonicで正常に動作しますが、サポートされていない場合があります。

* Windowsでは、 **コマンドプロンプト** と **PowerShell** がサポートされています。<a href="https://docs.microsoft.com/en-us/windows/wsl/faq" target="_blank">WSL</a>はIonicで動作することがわかっていますが、サポートされていない可能性があります。
* macOSでは、組み込みの **ターミナル** アプリがサポートされています。

Git Bash（<a href="https://git-scm.com" target="_blank">git-scm.com</a>）はTTY対話機能をサポートしておらず、Ionicはサポートしていません。

## Node と npm

モダンなJavaScriptプロジェクトのほとんどのツールは[Node.js](/docs/reference/glossary#node)で作られています。[ダウンロードページ](https://nodejs.org/en/download/)には、すべてのプラットフォームのインストールパッケージが事前に用意されています。互換性を確保するためにLTSバージョンを選択することをお勧めします。

NodeにはJavaScriptパッケージマネージャーである [npm](/docs/reference/glossary#npm) がバンドルされています。

インストールできているかを確認するためには、新しいターミナルウィンドウを開いて以下を実行します。

```shell
$ node --version
$ npm --version
```

> Permission errors are common on macOS when installing global packages with `npm`. If you get an `EACCES` error, see [Resolving Permission Errors](/docs/developing/tips#resolving-permission-errors).

## Git

必須ではありませんが、バージョン管理システムの[Git](/docs/reference/glossary#git)の利用を強くお勧めします。

Git is often accompanied by a Git Host, such as [GitHub](https://github.com/), in which case additional setup is required. Follow the tutorial from the Git Host's documentation to set up Git:

* GitHub: [Set up Git](https://help.github.com/en/articles/set-up-git)
* GitLab: [Installing Git](https://docs.gitlab.com/ee/topics/git/how_to_install_git)
* Bitbucket: [Install Git](https://www.atlassian.com/git/tutorials/install-git)

Otherwise, follow the [official installation instructions](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git). The command-line utility can be downloaded from the [download page](https://git-scm.com/downloads).

インストールできているかを確認するためには、新しいターミナルウィンドウを開いて以下を実行します。

```shell
$ git --version
```

### Git GUI

Gitはコマンドラインユーティリティですが、利用可能な [GUIクライアント](https://git-scm.com/downloads/guis/) は多数あります。[GitHub Desktop](https://desktop.github.com/)を推奨しており、GitHubとうまく連携します。
