# Automated Crafting

[灵感来源](https://www.spigotmc.org/resources/automated-crafting.70432/)

## 使用方法

第一步：放置一个投掷器(不是发射器)

![1.png](https://attachment.mcbbs.net/forum/201908/17/144756m50kp9e3wzk3fr2r.png)

第二步：在投掷器的侧面放置一个展示框

![2.png](https://attachment.mcbbs.net/forum/201908/17/144756vrroa9her9ay9qiw.png)

第三步：在展示框上放上你想自动合成的物品（以金镐为例）

![3.png](https://attachment.mcbbs.net/forum/201908/17/144756n0ccrj6k66ttm6cl.png)

第四步：在投掷器内部放入需要的材料（以金镐为例）

![4.png](https://attachment.mcbbs.net/forum/201908/17/144756fccvzcbtcscc81b1.png)

第五步：Enjoy!

注意一：给予红石信号时，它会暂停合成

注意二：如果投掷器所对的那一面正好有个箱子，合成出的物品会直接到箱子里，而不是丢出去（这样就无需使用漏斗这种烧游戏性能的东西了）

## 源码结构

| 函数 | 额外标签 | 用途 |
| :-: | :-: | :-- |
| autocrafting:init | load | 初始化函数，注册计分板等用 |
| autocrafting:search | tick | 搜索玩家附近的投掷器，并在未作标识的投掷器位置生成持久药水云 |
| autocrafting:test | tick | 用于对投掷器进行合法性检测，包括红石信号检测是否授权合成与删除无效的药水云 |
| autocrafting:read | tick | 同步药水云附近投掷器与物品展示框中的物品到计分板 |
| autocrafting:crafting | tick | 进行合成计算，将结果写回计分板 |
| autocrafting:write | tick | 将计分板计算出的新物品数量写回投掷器；如果投掷器正对方向有箱子，还会直接将合成出的物品写进箱子 |
| autocrafting:throw | tick | 如果计分板还记录了尚未丢出也尚未写入箱子的目标合成物品，那么就再模拟一次抛物 |
