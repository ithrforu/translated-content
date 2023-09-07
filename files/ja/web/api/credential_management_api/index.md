---
title: 資格情報管理 API
slug: Web/API/Credential_Management_API
l10n:
  sourceCommit: b280ea1234452ff553caa466bf532a66ba51db01
---

{{DefaultAPISidebar("Credential Management API")}}

資格情報管理 API を使用すると、ウェブサイトがユーザー、連携アカウント、公開鍵の資格情報を保存および取得することができます。これらの機能により、ユーザーはパスワードを入力せずにログインしたり、サイトへのログインに使用した連携アカウントを確認したり、期限切れのセッションに明示的なログインの手続きなしでセッションを再開したりすることができます。

## 資格情報管理の概念と使用方法

この API により、ウェブサイトがユーザーエージェントのパスワードシステムと直接対話できるようになるため、ウェブサイトはサイトの資格情報を統一した方法で扱うことができ、ユーザーエージェントは資格情報の管理でより良い支援を提供することができるようになります。例えば、ユーザエージェントは、連合アイデンティティプロバイダーや、ユーザー名とパスワードだけでなく、それ以上のものを使用する難解なログインメカニズムを扱うのに特に苦労しています。

これらの問題に対処するために、資格情報管理 API は、ウェブサイトがさまざまな種類の資格情報を保存したり取得したりする方法を提供しています。これによりユーザーは、サイトにログインするために使用した連携アカウントを確認したり、期限切れのセッションに明示的なログインの手続きなしでセッションを再開したりすることができます。

> **メモ:** この API は最上位のコンテキストのみに制限されています。 `get()` や `store()` を `<iframe>` 要素の中で呼び出すと、何もせずに解決します。

### サブドメイン間で共有される資格情報

より新しい版の仕様では、別のサブドメインから資格情報を取得できるようになっています。例えば、 `login.example.com` に保存されているパスワードを使用して `www.example.com` にログインすることができます。これを利用するには、{{domxref("CredentialsContainer.store()")}} を呼び出してパスワードを明示的に格納する必要があります。これは、公開接尾辞リスト (PSL) 照合と呼ばれることもあるりますが、仕様では、資格情報の有効なスコープを決定するために PSL を使用することを推奨しているだけです。必須ではありません。そのため、ブラウザーによって実装が異なる場合があります。

## インターフェイス

- {{domxref("Credential")}}
  - : 信頼の決定の前提条件として、エンティティに関する情報を提供します。
- {{domxref("CredentialsContainer")}}
  - : ログインやログアウトの成功などの興味深いイベントが発生したときに、資格情報を要求し、ユーザーエージェントに通知するメソッドを公開します。このインターフェイスは `navigator.credentials` からアクセスできます。
- {{domxref("FederatedCredential")}}
  - : ウェブサイトがユーザーを正しく認証するために信頼するエンティティである、連合アイデンティティプロバイダーからの資格情報に関する情報を提供し、また、そのための API を提供します。 [OpenID Connect](https://openid.net/developers/specs/) はそのようなフレームワークの一例です。
- {{domxref("PasswordCredential")}}
  - : ユーザー名/パスワードの組に関する情報を提供します。
- {{domxref("PublicKeyCredential")}}
  - : パスワードの代わりに、フィッシング不可能でデータ侵害に強い非対称キーペアを使用してログインするための資格情報を提供します。

## 仕様書

{{Specifications}}

## ブラウザーの互換性

{{Compat}}