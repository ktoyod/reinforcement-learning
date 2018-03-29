# 第5回 方策勾配法で迷路を攻略
強化学習のアルゴリズムの一種である**方策勾配法**を用いてエージェントが一直線にゴールへ向かうように方策を学習させる

## 強化学習の方法
1. 方策反復法
   - 方策にしたがって行動しゴールにたどり着いた時に、早くゴール出来たケースで実行した行動は重要だと考え、その行動を今後多く取り入れるように方策を更新する
   - うまく行ったケースの行動を重要視
   - 今回は方策反復法の具体的アルゴリズムである方策勾配法(Policy Gradient Method)を実装
2. 価値反復法
   - ゴールから逆算して、ゴールの１つ手前、２つ手前の状態へと順々に誘導していく
   - ゴール以外の状態にも価値をつける

## softmax関数による方策の実装
- `simple_convert_into_pi_from_theta` -> `softmax_convert_into_pi_from_theta`
- softmax関数を用いてθを変換する

## 方策勾配法に従い方策を更新
- [連載ページ](https://book.mynavi.jp/manatee/detail/id=88297)の数式の通り、方策を更新する

## 方策勾配法の理論
- 方策を表形式表現で表した場合、softmax関数を使用してパラメータかθから方策πへの変換を行うと、パラメータシータが負の値になっても確率が計算できる
- パラメータθの更新を方策勾配法で解くための**方策勾配定理**が存在
- 方策勾配定理を近似的に実装するREINFORCEアルゴリズムが存在

## 参考
- [Sutton, Richard S., et al. "Policy gradient methods for reinforcement learning with function approximation." Advances in neural information processing systems. 2000.](https://papers.nips.cc/paper/1713-policy-gradient-methods-for-reinforcement-learning-with-function-approximation.pdf)
- [これからの強化学習（著）牧野 貴樹ら 森北出版](https://www.amazon.co.jp/%E3%81%93%E3%82%8C%E3%81%8B%E3%82%89%E3%81%AE%E5%BC%B7%E5%8C%96%E5%AD%A6%E7%BF%92-%E7%89%A7%E9%87%8E-%E8%B2%B4%E6%A8%B9/dp/4627880316)
- [最強囲碁AI アルファ碁 解体新書 深層学習、モンテカルロ木探索、強化学習から見たその仕組み（著）大槻 知史 翔泳社](https://www.amazon.co.jp/%E6%9C%80%E5%BC%B7%E5%9B%B2%E7%A2%81AI-%E3%82%A2%E3%83%AB%E3%83%95%E3%82%A1%E7%A2%81-%E8%A7%A3%E4%BD%93%E6%96%B0%E6%9B%B8-%E6%B7%B1%E5%B1%A4%E5%AD%A6%E7%BF%92%E3%80%81%E3%83%A2%E3%83%B3%E3%83%86%E3%82%AB%E3%83%AB%E3%83%AD%E6%9C%A8%E6%8E%A2%E7%B4%A2%E3%80%81%E5%BC%B7%E5%8C%96%E5%AD%A6%E7%BF%92%E3%81%8B%E3%82%89%E8%A6%8B%E3%81%9F%E3%81%9D%E3%81%AE%E4%BB%95%E7%B5%84%E3%81%BF-%E5%A4%A7%E6%A7%BB-ebook/dp/B073J6KRFZ)
