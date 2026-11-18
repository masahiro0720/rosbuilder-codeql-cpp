# 第5回：ROSBuilder 生成C++パッケージのCodeQL比較実習

このZIPには、ユーザーから提供されたサンプルZIP中の
`generated_sample_template_package/eval1_minimal/cpp/template/eval1_minimal_cpp_pkg_project/`
の内容を**無変更で**収録しています。

追加したファイルは次の2個だけです。

- `.github/workflows/codeql-cpp-none.yml`
  - Pushしたときに自動実行。
  - `build-mode: none`。ROS 2はインストールせず、ビルドしません。
- `.github/workflows/codeql-cpp-manual.yml`
  - **手動実行のみ**。
  - `build-mode: manual`。Ubuntu 24.04、ROS 2 Jazzy、`colcon build`を使用します。

## 使用手順

1. このZIPを展開し、展開先の **中身** を新規公開GitHubリポジトリ
   `rosbuilder-codeql-cpp` のルートへアップロードします。
2. `.github/workflows/` に2つのYAMLがあることを確認します。
3. `Actions > ROSBuilder C++ CodeQL - No Build` の自動実行結果を確認します。
4. `Security and quality > Code scanning` の結果を記録します。
5. `Actions > ROSBuilder C++ CodeQL - Manual Build (Jazzy)` を開き、
   `Run workflow` ボタンから手動実行します。
6. `Build ROS 2 packages while CodeQL traces compilation` と `Perform CodeQL Analysis`
   の結果・実行時間・警告・アラートを記録し比較します。

## 実験に関する注意

- `manual`にはROS 2 Jazzyのセットアップが入るため、`none`よりも実行時間が長くなる可能性があります。
- `ros-tooling/setup-ros@v0.7`の`required-ros-distributions: jazzy`は
  ROS 2 Jazzyのdesktop構成をインストールします。セットアップ時にAPTの一時的な問題が発生する場合があります。
- GitHub Actionsの成功は、実際のLifecycleNodeの正常動作を保証しません。
- Code scanningでアラート0件でも、すべての不具合が存在しないことを保証しません。
- 複数のCodeQL実行を区別するため、解析結果の`category`を別々に設定しています。
- 公開リポジトリに載せる前に、共同研究資料の公開可否・ライセンスを確認してください。
