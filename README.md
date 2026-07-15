# 外卖订餐系统

基于 Android 平台的外卖订餐应用，支持用户注册登录、浏览美食、选择规格、购物车管理和订单提交等功能。

## 功能特性

- **用户认证**：注册、登录功能
- **美食浏览**：首页展示各类美食，支持下拉刷新
- **规格选择**：每种美食提供多种规格选项（小份/中份/大份等），价格随规格变化
- **购物车管理**：添加商品、增减数量、删除商品
- **订单提交**：查看购物车、提交订单、查看历史订单

## 技术栈

- **语言**：Java 8
- **框架**：AndroidX、Material Design
- **图片加载**：Glide 4.13.0
- **数据库**：SQLite（本地存储）
- **构建工具**：Gradle 4.2.1

## 项目结构

```
app/src/main/
├── java/njust/dzh/ordersystem/
│   ├── Activity/          # 活动页面
│   │   ├── WelcomeActivity.java    # 欢迎页
│   │   ├── LoginActivity.java      # 登录页
│   │   ├── RegisterActivity.java   # 注册页
│   │   ├── MainActivity.java       # 主页面
│   │   ├── FoodActivity.java       # 美食详情页（含规格选择）
│   │   └── OrderActivity.java      # 订单页
│   ├── Fragment/          # 碎片
│   │   ├── HomeFragment.java       # 首页碎片
│   │   ├── CartFragment.java       # 购物车碎片
│   │   └── PersonFragment.java     # 个人中心碎片
│   ├── Bean/              # 数据模型
│   │   ├── Food.java               # 美食实体（含规格信息）
│   │   ├── Cart.java               # 购物车实体（含规格）
│   │   ├── Order.java              # 订单实体
│   │   └── User.java               # 用户实体
│   ├── Adapter/           # 适配器
│   │   ├── FoodAdapter.java        # 美食列表适配器
│   │   ├── CartAdapter.java        # 购物车适配器
│   │   └── OrderAdapter.java       # 订单列表适配器
│   └── DataBase/          # 数据库操作
│       ├── DataBaseHelper.java     # 数据库助手
│       ├── FoodDao.java            # 美食数据访问
│       ├── CartDao.java            # 购物车数据访问
│       ├── OrderDao.java           # 订单数据访问
│       └── UserDao.java            # 用户数据访问
└── res/                   # 资源文件
    ├── layout/            # 布局文件
    ├── drawable/          # 图片资源
    └── values/            # 配置文件
```

## 核心功能实现

### 规格选择

在 [FoodActivity.java](file:///c:/Users/32003/Desktop/202319120530-朱咏颖/Food delivery/app/src/main/java/njust/dzh/ordersystem/Activity/FoodActivity.java) 中实现了规格选择功能：

- 通过 RadioGroup 动态生成规格选项
- 默认选中第一个规格
- 添加购物车前验证是否选择了规格
- 不同规格对应不同价格

### 数据库设计

购物车表（Cart）包含以下字段：
- `name`：美食名称
- `imageId`：图片ID
- `price`：价格
- `num`：数量
- `size`：规格（新增）

复合主键为 `(name, size)`，允许同一美食不同规格独立存在于购物车中。

## 快速开始

### 环境要求

- JDK 1.8+
- Android Studio 4.2+
- Android SDK 21+

### 运行步骤

1. 克隆项目到本地
2. 使用 Android Studio 打开项目
3. 等待 Gradle 同步完成
4. 连接 Android 设备或启动模拟器
5. 点击 Run 按钮运行应用

## 数据说明

### 美食数据

应用内置了 12 种美食数据，包含：
- 口水鸡、满杯百香果、巴西烤肉披萨
- 龙门花甲、美味炸鸡、煎饼果子
- 黄焖鸡米饭、西施烤肉饭、十三香龙虾
- 招牌辣子鸡、招牌无骨炸鸡、红烧排骨饭

每种美食都配置了对应的规格和价格。

### 数据库版本

数据库版本已升级至 v2，新增了规格字段。首次运行时会自动创建新的数据库表结构。

## 许可证

MIT License
