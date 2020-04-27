# ion-refresher

RefresherはContentコンポーネント引っ張って更新する機能を提供します。
ユーザーはより多くのデータを取得するために、
タッチ操作でリストを引っ張って更新できます。

データはRefresherの外部のイベントで更新すべきです。
一回の非同期処理が完了すれば、`complete()`を呼び出すことで、
Refresherも終了するべきです。

### Native Refreshers

Both iOS and Android platforms provide refreshers that take advantage of properties exposed by their respective devices that give pull to refresh a fluid, native-like feel.

Certain properties such as `pullMin` and `snapbackDuration` are not compatible because much of the native refreshers are scroll-based. See [Refresher Properties](#properties) for more information.

#### iOS Usage

Using the iOS native `ion-refresher` requires setting the `pullingIcon` property on `ion-refresher-content` to the value of one of the available spinners. See the [Spinner Documentation](../spinner#properties) for accepted values. The `pullingIcon` defaults to the `lines` spinner on iOS. The spinner tick marks will be progressively shown as the user pulls down on the page.

The iOS native `ion-refresher` relies on rubber band scrolling in order to work properly and is only compatible with iOS devices as a result. We provide a fallback refresher for apps running in iOS mode on devices that do not support rubber band scrolling.

#### Android Usage

Using the MD native `ion-refresher` requires setting the `pullingIcon` property on `ion-refresher-content` to the value of one of the available spinners. See the [ion-spinner Documentation](../spinner#properties) for accepted values. `pullingIcon` defaults to the `circular` spinner on MD.

