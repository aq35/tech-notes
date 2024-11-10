Zscalerによるブロックを確認する方法をいくつか示します：

1. **詳細なcurlの実行**
```bash
# より詳細なエラー情報を表示
curl -v -L https://download.docker.com/linux/ubuntu/gpg

# プロキシ情報を明示的に指定して確認
curl -v -x http://proxy.zscaler.com:port https://download.docker.com/linux/ubuntu/gpg
```

2. **Windowsでの確認**
```powershell
# Zscalerのログを確認（管理者権限が必要）
Event Viewer > Applications and Services Logs > Zscaler
```

3. **ブラウザでの確認**
```plaintext
1. 同じURLをブラウザで開く
2. F12開発者ツールを開く
3. Networkタブで通信を確認
4. Zscalerのブロックページやエラーメッセージを確認
```

4. **プロキシの応答確認**
```bash
# OpenSSLを使用して詳細な通信確認
openssl s_client -connect download.docker.com:443 -servername download.docker.com

# Telnetでプロキシ接続確認
telnet proxy.zscaler.com port
```

これらの方法で得られたエラーメッセージや応答から、Zscalerによるブロックかどうかを判断できます。特に、Zscaler特有のエラーメッセージや応答コードが表示されるはずです。