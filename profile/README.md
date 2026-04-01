# Vendure Plugins Platform 分类总览

## 主题与项目组命名总表

| 当前主题    | 组代号        | 中文名字建议   | Repo Short Desc                                                     |
| ----------- | ------------- | -------------- | ------------------------------------------------------------------- |
| Hub Core    | `hub-core`    | 核心基础组     | Core platform infrastructure and extension runtime.                 |
| Hub Base    | `hub-base`    | 基础类库组     | Shared open libraries, utilities, and testing foundations.          |
| Hub Dev     | `hub-dev`     | 开发工具组     | Internal developer tools and local workflow utilities.              |
| Hub Store   | `hub-store`   | 前台交易组     | Storefront commerce features for shopping and orders.               |
| Hub Auth    | `hub-auth`    | 认证身份组     | Authentication, identity, and account access integrations.          |
| Hub Pay     | `hub-pay`     | 支付账单组     | Payments, billing, invoicing, and money-related capabilities.       |
| Hub Ship    | `hub-ship`    | 物流履约对接组 | Shipping, fulfillment, carrier integration, and tracking workflows. |
| Hub ERP     | `hub-erp`     | 供应链 ERP 组  | ERP and supply chain operations for inventory and procurement.      |
| Hub Search  | `hub-search`  | 搜索组         | Search infrastructure, indexing, and discovery experiences.         |
| Hub Content | `hub-content` | 内容管理组     | Content, SEO, widgets, and merchandising presentation tools.        |
| Hub Growth  | `hub-growth`  | 增长营销组     | Growth, campaigns, loyalty, and customer engagement features.       |
| Hub Report  | `hub-report`  | 数据报表组     | Reporting, metrics, analytics, and business insights.               |
| Hub Support | `hub-support` | 客服支持组     | Customer support, service operations, and risk handling tools.      |
| Hub Glass   | `hub-glass`   | 眼镜业务组     | Vertical solutions for optical and eyewear commerce.                |

## 一、Platform Layer（平台层）

### ⚙️ Hub Core（基础设施与运维）

| Package                         | 说明                                                                                                                    |
| ------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| `hps-plugin-hub`                | 插件市场服务端开放能力，承载插件授权与认证。                                                                            |
| `hps-plugin-hub-client`         | 插件市场客户端能力，用于接入授权与认证流程。                                                                            |
| `hps-plugin-hub-verdaccio`      | 插件分发仓库能力（Verdaccio），支撑市场发布链路。                                                                       |
| `hps-plugin-admin`              | 后台管理系统容器，其他插件可基于它扩展菜单、模块和功能。                                                                |
| `hps-plugin-core`               | 插件体系核心能力与基础抽象。                                                                                            |
| `hps-plugin-setting`            | 配置项与系统设置管理能力。                                                                                              |
| `hps-plugin-storage`            | 文件与对象存储集成能力。                                                                                                |
| `hps-plugin-data-aggregation`   | 可扩展数据聚合容器能力，并按需进行缓存编排与性能优化, 如果首页 banner, new Arrivals, best seller, review 等数据集缓存。 |
| `hps-plugin-email`              | 基础邮件发送与模板通知能力，供各业务插件接入复用。                                                                      |
| `hps-plugin-token-active-order` | 客户端订单服务器端流程执行的基础机制，支持通过 token 参数调用订单相关服务端逻辑。                                       |

### 🏛️ Hub Base（基础免费库，对外开放）

| Package       | 说明                                             |
| ------------- | ------------------------------------------------ |
| `hps-common`  | 插件公共类库，提供通用工具与类型，免费开放集成。 |
| `hps-testing` | 插件测试类库，提供测试基础能力，免费开放集成。   |
| `hps-dev-kits` | Hps Admin的 UI 开发工具包。   |


### 🛠️ Hub Dev（内部工具，不对外）

| Package      | 说明                 |
| ------------ | -------------------- |
| `dev-server` | 本地开发服务器能力。 |

## 二、Business Capabilities（业务能力层）

### 🛒 Hub Store（前台与订单上下文）

| Package                             | 说明                         |
| ----------------------------------- | ---------------------------- |
| `hps-plugin-favorites`              | 商品收藏/心愿单能力。        |
| `hps-plugin-product-recommendation` | 商品推荐能力。               |
| `hps-plugin-review`                 | 商品评价/评论能力。          |
| `hps-plugin-stock-monitor`          | 库存监控与补货提醒能力。     |
| `hps-plugin-public-customer-groups` | 公共客户分组能力。           |
| `hps-plugin-digital-product`        | 虚拟数字商品展示与销售能力。 |

### 🔐 Hub Auth（认证与身份）

| Package                  | 说明                    |
| ------------------------ | ----------------------- |
| `hps-plugin-auth-code`   | 验证码认证能力。        |
| `hps-plugin-auth-github` | GitHub OAuth 登录能力。 |
| `hps-plugin-auth-google` | Google OAuth 登录能力。 |

### 💳 Hub Pay（支付与账单）

| Package                     | 说明                                                 |
| --------------------------- | ---------------------------------------------------- |
| `hps-plugin-payment-core`   | 支付能力核心抽象。                                   |
| `hps-plugin-payment-paypal` | PayPal 支付集成。                                    |
| `hps-plugin-payment-stripe` | Stripe 支付集成。                                    |
| `hps-plugin-reward-points`  | 积分奖励体系能力。                                   |
| `hps-plugin-digital-card`   | 数字卡券/礼品卡能力。                                |
| `hps-plugin-invoice`        | 订单账单与发票生成能力，支持客户下载与开票数据管理。 |

### 🚚 Hub Ship（物流履约与渠道对接）

| Package                               | 说明                                                               |
| ------------------------------------- | ------------------------------------------------------------------ |
| `hps-plugin-shipping-tiered-pricing`  | C 端分层/阶梯式运费定价与配送方式选择能力。                        |
| `hps-plugin-shipping-carrier-adapter` | B 端物流公司对接适配能力，统一承运商接口并支持多渠道扩展接入。     |
| `hps-plugin-shipping-tracking`        | 物流运单追踪与状态回传能力，支持轨迹同步、签收状态更新与异常预警。 |

### 🏭 Hub ERP（供应链与ERP）

| Package                | 说明                                                                         |
| ---------------------- | ---------------------------------------------------------------------------- |
| `hps-plugin-inventory` | 供应链库存 ERP 管理，支持进货跟踪、在途库存、实际库存与供应商商品 SKU 管理。 |

### 🔎 Hub Search（搜索）

| Package                   | 说明                              |
| ------------------------- | --------------------------------- |
| `hps-plugin-typesense`    | Typesense 搜索集成能力。          |
| `hps-plugin-smart-search` | 智能搜索与检索增强能力。          |
| `hps-plugin-cmdk`         | 聚合前端 Command+K 搜索内容能力。 |

### 🗂️ Hub Content（内容管理）

| Package                  | 说明                             |
| ------------------------ | -------------------------------- |
| `hps-plugin-metas`       | SEO 元信息管理能力。             |
| `hps-plugin-banner`      | Banner 位与运营展示能力。        |
| `hps-plugin-topic`       | 话题/内容模块能力。              |
| `hps-plugin-help-center` | 帮助中心内容管理能力。           |
| `hps-plugin-view-widget` | 页面可视化组件/小部件能力。      |
| `hps-plugin-showcase`    | 对外展示当前生产项目与落地案例。 |

### 📣 Hub Growth（营销与增长）

| Package                      | 说明                                                            |
| ---------------------------- | --------------------------------------------------------------- |
| `hps-plugin-campaign`        | 营销活动编排与执行能力。                                        |
| `hps-plugin-subscribe`       | 订阅与触达管理能力。                                            |
| `hps-plugin-email-marketing` | 营销邮件模板管理与批量发送能力。                                |
| `hps-plugin-points-shop`     | 积分兑换商城，支持积分兑换、购买、兑换券与特殊商品购买。        |
| `hps-plugin-reward-referral` | 邀请与推荐奖励能力。                                            |
| `hps-plugin-ugc`             | 用户创作内容能力，支持活动市场、任务领取、奖励获取与内容审核。  |
| `hps-plugin-feed`            | 生成标准商品 Feed 内容，用于 Facebook/Meta 与 Google 广告投放。 |
| `hps-plugin-sitemap`         | 生成标准 Sitemap/索引内容，支持广告与搜索平台内容抓取。         |

### 📊 Hub Report（分析与报表）

| Package                | 说明                                             |
| ---------------------- | ------------------------------------------------ |
| `hps-plugin-metrics`   | 销售指标图表与报表展示能力。                     |
| `hps-plugin-reporting` | 成本、价格、利润及日销售、月销售等经营数据计算。 |

### 🎫 Hub Support（客户支持）

| Package                     | 说明                                                               |
| --------------------------- | ------------------------------------------------------------------ |
| `hps-plugin-ticket`         | 工单系统能力。                                                     |
| `hps-plugin-assisted-order` | 辅助用户进行代下单能力。                                           |
| `hps-plugin-risk-control`   | 记录失信客户，识别并跟踪潜在发货配送风险、退款风险与恶意退单用户。 |

### 🕶️ Hub Glass（行业/垂直场景）

| Package                  | 说明               |
| ------------------------ | ------------------ |
| `glass-plugin-tryon`     | 眼镜 AR 试戴能力。 |
| `glass-plugin-dimension` | 眼镜尺寸管理能力。 |
| `glass-plugin-lens-flow` | 镜片相关业务能力。 |
