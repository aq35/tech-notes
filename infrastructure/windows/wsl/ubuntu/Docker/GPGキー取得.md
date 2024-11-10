GPGキー問題を現在の状態から解決するための方法を検討します：

1. **代替経路でのGPGキー取得**
```bash
# Windowsホストで取得
# PowerShellまたはブラウザでダウンロード
# その後、WSLに転送
curl.exe -o docker.gpg https://download.docker.com/linux/ubuntu/gpg
copy docker.gpg \\wsl$\Ubuntu\tmp\

# WSL側で使用
sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg /tmp/docker.gpg
```

2. **curl オプション変更で詳細調査**
```bash
# より詳細なエラー情報取得
curl -v -L https://download.docker.com/linux/ubuntu/gpg

# プロキシ設定を明示的に指定
curl -x http://proxy.company.com:port -L https://download.docker.com/linux/ubuntu/gpg

# SSL検証をスキップ（開発環境のみ）
curl -k -L https://download.docker.com/linux/ubuntu/gpg
```

3. **IT部門からの支援**
```plaintext
- GPGキーファイルの直接提供を依頼
- 社内で承認された取得方法の確認
- 必要に応じてZscalerのポリシー調整
```

まずは詳細なエラー調査を行い、その結果に基づいて適切な対応を選択することをお勧めします。Windows側での代替取得が最も現実的な解決策かもしれません。