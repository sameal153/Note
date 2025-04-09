文章出处——https://juejin.cn/post/
https://juejin.cn/post/7250513276236808229?from=search-suggest
***
# 1 分层思想

计算机领域有一句话：计算机中任何问题都可通过增加一个虚拟层解决。这句体现了分层思想重要性，分层思想同样适用于Java工程架构。

分层优点是每层只专注本层工作，可以类比设计模式单一职责原则，或者经济学比较优势原理，每层只做本层最擅长的事情。

分层缺点是层之间通信时，需要通过适配器，翻译成本层或者下层可以理解的信息，通信成本有所增加。

我认为工程分层需要从五个维度思考：
#### (1) 单一

每层只处理一类事情，满足单一职责原则

#### (2) 降噪

信息在每一层进行传输，满足最小知识原则，只向下层传输必要信息

#### (3) 适配

每层都需要一个适配器，翻译信息为本层或者下层可以理解的信息

#### (4) 业务

业务对象可以整合业务逻辑，例如使用充血模型整合业务

#### (5) 数据

数据对象尽量纯净，尽量不要聚合业务


## 1.2 九层结构

综上所述SpringBoot工程可以分为九层：

- 工具层：util
	- 工具层承载工具代码。不依赖本项目其它模块，只依赖一些通用工具包
	
- 整合层：integration
	- 可能会依赖外部服务，那么将外部DTO转换为自己项目可以理解的对象，需要在integration层处理
	
- 基础层：infrastructure
	- 基础层核心是承载数据访问，entity实体对象承载在本层。只依赖工具模块
	
- 服务层：service
	- 核心代码
	
- 领域层：domain
	- 领域对象需要体现业务含义（领域对象采用充血模型聚合业务）、业务对象
	- 业务层可以更加灵活组合不同领域业务，并且可以增加流控、监控、日志、权限，分布式锁等控制，相较于领域层功能更为丰富
	
- 门面层：facade
	- 承载对外服务
	
- 控制层：controller
	- 作为本项目HTTP接口提供服务，供前端调用
	
- 客户端：client
	- 承载数据对外传输对象DTO
	
- 启动层：boot

  ![image.png](https://raw.githubusercontent.com/sameal153/PicturePool/master/PicturePool/laptop202404241807701.webp)

  ![image.png](https://raw.githubusercontent.com/sameal153/PicturePool/master/PicturePool/laptop202404241808634.webp)



# 理解Spring Boot设计思路

了解Spring Boot的设计思路可以帮助我们更好地理解和应用该框架

1. 约定优于配置：Spring Boot通过约定来减少开发者需要手动配置的内容。例如，Spring Boot可以根据环境变量自动配置数据库连接池等组件。
2. 自动配置：Spring Boot通过自动配置来简化开发过程。它通过扫描应用程序中的各种组件，并根据需要自动配置它们。这使得开发者可以更加专注于实现业务逻辑。
3. 面向切面编程（AOP）：Spring Boot支持面向切面编程，使得开发者可以更加轻松地实现跨模块的功能，如日志记录、性能监控等。
4. 分布式部署：Spring Boot支持分布式部署，使得应用程序可以更加轻松地扩展和部署到不同的服务器上。

# 反思总结

1. 了解Spring Boot的核心概念：在阅读Spring Boot工程之前，我们需要先了解其核心概念，如依赖注入、面向切面编程等。这有助于我们更好地理解工程中的各个组件和代码实现。
2. 关注工程的结构和组织：阅读Spring Boot工程时，我们需要关注其结构和组织方式。这有助于我们更好地理解各个模块的功能和作用，以及代码的组织方式。
3. 学习如何使用构建工具：构建工具（如Maven、Gradle）是管理Spring Boot工程的重要工具。我们需要学习如何使用这些构建工具来管理依赖项、构建应用程序等操作。
4. 分析代码实现：阅读Spring Boot工程的代码实现可以帮助我们更好地理解其工作原理和实现方式。我们可以分析代码中的注解、配置文件、控制器、服务等组件，以了解其功能和作用。
5. 深入了解核心模块：为了更好地应用Spring Boot框架，我们需要深入了解其核心模块，如自动配置、面向切面编程等。这有助于我们更加熟练地应用该框架，并实现更加复杂的功能。
6. 结合实际项目经验：阅读Spring Boot工程的同时，我们需要结合实际项目经验来理解和应用该框架。


# 2 分层详解

创建测试项目user-demo-service：

```xml
user-demo-service 
-user-demo-service-boot 
-user-demo-service-client 
-user-demo-service-controller 
-user-demo-service-domain 
-user-demo-service-facade 
-user-demo-service-infrastructure 
-user-demo-service-integration 
-user-demo-service-service 
-user-demo-service-util
```
## 2.1 util

工具层承载工具代码

不依赖本项目其它模块

只依赖一些通用工具包

xml

复制代码
```xml
user-demo-service-util
    -/src/main/java
        -date
            -DateUtil.java
        -json
            -JSONUtil.java
        -validate
            -BizValidator.java

```
## 2.2 infrastructure

基础层核心是承载数据访问，entity实体对象承载在本层。
### 2.2.1 项目结构

代码层分为两个领域：

- player：运动员
- game：比赛

每个领域具有两个子包：

- entity
- mapper

xml

复制代码

```xml
user-demo-service-infrastructure
    -/src/main/java
        -player
            -entity
                -PlayerEntity.java
            -mapper
                -PlayerEntityMapper.java
        -game
            -entity
                -GameEntity.java
            -mapper
                -GameEntityMapper.java
    -/src/main/resources
        -mybatis
            -sqlmappers
                -gameEntityMapper.xml
                -playerEntityMapper.xml

```

  

### 2.2.2 本项目间依赖关系

infrastructure只依赖工具模块

text

复制代码

```text
<dependency>
    <groupId>com.test.javafront</groupId>
    <artifactId>user-demo-service-util</artifactId>
</dependency>
```

  

### 2.2.3 核心代码

创建运动员数据表：
```sql
CREATE TABLE `player` (
  `id` bigint(20) NOT NULL AUTO_INCREMENT COMMENT '主键',
  `player_id` varchar(256) NOT NULL COMMENT '运动员编号',
  `player_name` varchar(256) NOT NULL COMMENT '运动员名称',
  `height` int(11) NOT NULL COMMENT '身高',
  `weight` int(11) NOT NULL COMMENT '体重',
  `game_performance` text COMMENT '最近一场比赛表现',
  `creator` varchar(256) NOT NULL COMMENT '创建人',
  `updator` varchar(256) NOT NULL COMMENT '修改人',
  `create_time` datetime NOT NULL COMMENT '创建时间',
  `update_time` datetime NOT NULL COMMENT '修改时间',
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=1 DEFAULT CHARSET=utf8

```
运动员实体对象，gamePerformance字段作为string保存在数据库，这体现了数据层尽量纯净，不要整合过多业务，解析任务应该放在业务层：


```java
public class PlayerEntity {
    private Long id;
    private String playerId;
    private String playerName;
    private Integer height;
    private Integer weight;
    private String creator;
    private String updator;
    private Date createTime;
    private Date updateTime;
    private String gamePerformance;
}


```
运动员Mapper对象：

```java
@Repository
public interface PlayerEntityMapper {
    int insert(PlayerEntity record);
    int updateById(PlayerEntity record);
    PlayerEntity selectById(@Param("playerId") String playerId);
}
```


## 2.3 domain

### 2.3.1 概念说明

领域层是DDD流行兴起之概念

可以通过三组对比理解领域层

- 领域对象 VS 数据对象
- 领域对象 VS 业务对象
- 领域层 VS 业务层

  

#### (1) 领域对象 VS 数据对象

数据对象字段尽量纯净，使用基本类型

```java
public class PlayerEntity {
    private Long id;
    private String playerId;
    private String playerName;
    private Integer height;
    private Integer weight;
    private String creator;
    private String updator;
    private Date createTime;
    private Date updateTime;
    private String gamePerformance;
}

```

以查询结果领域对象为例

领域对象需要体现业务含义
```java
public class PlayerQueryResultDomain {
    private String playerId;
    private String playerName;
    private Integer height;
    private Integer weight;
    private GamePerformanceVO gamePerformance;
}

public class GamePerformanceVO {
    // 跑动距离
    private Double runDistance;
    // 传球成功率
    private Double passSuccess;
    // 进球数
    private Integer scoreNum;
}
```

  

#### (2) 领域对象 VS 业务对象

业务对象同样会体现业务，领域对象和业务对象有什么不同呢？其中一个最大不同是领域对象采用充血模型聚合业务。

运动员新增业务对象：
```java
public class PlayerCreateBO {
    private String playerName;
    private Integer height;
    private Integer weight;
    private GamePerformanceVO gamePerformance;
    private MaintainCreateVO maintainInfo;
}

```
运动员新增领域对象：

```java
public class PlayerCreateDomain implements BizValidator {
    private String playerName;
    private Integer height;
    private Integer weight;
    private GamePerformanceVO gamePerformance;
    private MaintainCreateVO maintainInfo;

    @Override
    public void validate() {
        if (StringUtils.isEmpty(playerName)) {
            throw new BizException(ErrorCodeBizEnum.ILLEGAL_ARGUMENT);
        }
        if (null == height) {
            throw new BizException(ErrorCodeBizEnum.ILLEGAL_ARGUMENT);
        }
        if (height > 300) {
            throw new BizException(ErrorCodeBizEnum.ILLEGAL_ARGUMENT);
        }
        if (null == weight) {
            throw new BizException(ErrorCodeBizEnum.ILLEGAL_ARGUMENT);
        }
        if (null != gamePerformance) {
            gamePerformance.validate();
        }
        if (null == maintainInfo) {
            throw new BizException(ErrorCodeBizEnum.ILLEGAL_ARGUMENT);
        }
        maintainInfo.validate();
    }
}
```

  

#### (3) 领域层 VS 业务层

领域层和业务层都包含业务，二者不是替代关系，而是互补关系。业务层可以更加灵活组合不同领域业务，并且可以增加流控、监控、日志、权限，分布式锁等控制，相较于领域层功能更为丰富。

  

### 2.3.2 项目结构

代码层分为两个领域：

- player：运动员
- game：比赛

每个领域具有三个子包：

- domain：领域对象
- event：领域事件
- vo：值对象
```xml
user-demo-service-domain
    -/src/main/java
        -base
            -domain
                -BaseDomain.java
            -event
                -BaseEvent.java
            -vo
                -BaseVO.java
                -MaintainCreateVO.java
                -MaintainUpdateVO.java
        -player
            -domain
                -PlayerCreateDomain.java
                -PlayerUpdateDomain.java
                -PlayerQueryResultDomain.java
            -event
                -PlayerUpdateEvent.java
            -vo
                -GamePerformanceVO.java
        -game
            -domain
                -GameCreateDomain.java
                -GameUpdateDomain.java
                -GameQueryResultDomain.java
            -event
                -GameUpdateEvent.java
            -vo
                -GameSubstitutionVO.java

```
### 2.3.3 本项目间依赖关系

domain依赖本项目两个模块：

- util
- client

之所以依赖client模块是因为领域对象聚合了业务校验，以下信息需要暴露至外部：

- BizException
- ErrorCodeBizEnum
```xml
<dependency>
    <groupId>com.test.javafront</groupId>
    <artifactId>user-demo-service-util</artifactId>
</dependency>
<dependency>
    <groupId>com.test.javafront</groupId>
    <artifactId>user-demo-service-client</artifactId>
</dependency>

```

### 2.3.4 核心代码

以运动员修改领域对象为例：

```java
// 运动员修改领域对象
public class PlayerUpdateDomain extends BaseDomain implements BizValidator {
    private String playerId;
    private String playerName;
    private Integer height;
    private Integer weight;
    private String updator;
    private Date updatetime;
    private GamePerformanceVO gamePerformance;
    private MaintainUpdateVO maintainInfo;

    @Override
    public void validate() {
        if (StringUtils.isEmpty(playerId)) {
            throw new BizException(ErrorCodeBizEnum.ILLEGAL_ARGUMENT);
        }
        if (StringUtils.isEmpty(playerName)) {
            throw new BizException(ErrorCodeBizEnum.ILLEGAL_ARGUMENT);
        }
        if (null == height) {
            throw new BizException(ErrorCodeBizEnum.ILLEGAL_ARGUMENT);
        }
        if (height > 300) {
            throw new BizException(ErrorCodeBizEnum.ILLEGAL_ARGUMENT);
        }
        if (null == weight) {
            throw new BizException(ErrorCodeBizEnum.ILLEGAL_ARGUMENT);
        }
        if (null != gamePerformance) {
            gamePerformance.validate();
        }
        if (null == maintainInfo) {
            throw new BizException(ErrorCodeBizEnum.ILLEGAL_ARGUMENT);
        }
        maintainInfo.validate();
    }
}

// 比赛表现值对象
public class GamePerformanceVO implements BizValidator {

    // 跑动距离
    private Double runDistance;
    // 传球成功率
    private Double passSuccess;
    // 进球数
    private Integer scoreNum;

    @Override
    public void validate() {
        if (null == runDistance) {
            throw new BizException(ErrorCodeBizEnum.ILLEGAL_ARGUMENT);
        }
        if (null == passSuccess) {
            throw new BizException(ErrorCodeBizEnum.ILLEGAL_ARGUMENT);
        }
        if (Double.compare(passSuccess, 100) > 0) {
            throw new BizException(ErrorCodeBizEnum.ILLEGAL_ARGUMENT);
        }
        if (null == runDistance) {
            throw new BizException(ErrorCodeBizEnum.ILLEGAL_ARGUMENT);
        }
        if (null == scoreNum) {
            throw new BizException(ErrorCodeBizEnum.ILLEGAL_ARGUMENT);
        }
    }
}

// 修改人值对象
public class MaintainUpdateVO implements BizValidator {

    // 修改人
    private String updator;
    // 修改时间
    private Date updateTime;

    @Override
    public void validate() {
        if (null == updator) {
            throw new BizException(ErrorCodeBizEnum.ILLEGAL_ARGUMENT);
        }
        if (null == updateTime) {
            throw new BizException(ErrorCodeBizEnum.ILLEGAL_ARGUMENT);
        }
    }
}

```
## 2.4 service

### 2.4.1 项目结构

```xml
user-demo-service-service
    -/src/main/java
        -player
            -adapter
                -PlayerServiceAdapter.java
            -event
                -PlayerMessageSender.java
            -service
                -PlayerService.java
        -game
            -adapter
                -GameServiceAdapter.java
            -event
                -GameMessageSender.java
            -service
                -GameService.java

```
### 2.4.2 本项目间依赖关系

service依赖本项目四个模块：

- util
- domain
- integration
- infrastructure
```xml
<dependency>
    <groupId>com.test.javafront</groupId>
    <artifactId>user-demo-service-domain</artifactId>
</dependency>
<dependency>
    <groupId>com.test.javafront</groupId>
    <artifactId>user-demo-service-infrastructure</artifactId>
</dependency>
<dependency>
    <groupId>com.test.javafront</groupId>
    <artifactId>user-demo-service-util</artifactId>
</dependency>
<dependency>
    <groupId>com.test.javafront</groupId>
    <artifactId>user-demo-service-integration</artifactId>
</dependency>

```

  

### 2.4.3 核心代码

以运动员编辑服务为例：

```java
// 运动员服务
public class PlayerService {

    @Resource
    private PlayerEntityMapper playerEntityMapper;
    @Resource
    private PlayerMessageSender playerMessageSender;
    @Resource
    private PlayerServiceAdapter playerServiceAdapter;

    public boolean updatePlayer(PlayerUpdateDomain player) {
        AssertUtil.notNull(player, new BizException(ErrorCodeBizEnum.ILLEGAL_ARGUMENT));
        player.validate();
        PlayerEntity entity = playerServiceAdapter.convertUpdate(player);
        playerEntityMapper.updateById(entity);
        playerMessageSender.sendPlayerUpdatemessage(player);
        return true;
    }
}

// 运动员消息服务
public class PlayerMessageSender {

    @Resource
    private PlayerServiceAdapter playerServiceAdapter;

    public boolean sendPlayerUpdatemessage(PlayerUpdateDomain domain) {
        PlayerUpdateEvent event = playerServiceAdapter.convertUpdateEvent(domain);
        log.info("sendPlayerUpdatemessage event={}", event);
        return true;
    }
}

// 服务适配器
public class PlayerServiceAdapter {

    // domain -> entity
    public PlayerEntity convertUpdate(PlayerUpdateDomain domain) {
        PlayerEntity player = new PlayerEntity();
        player.setPlayerId(domain.getPlayerId());
        player.setPlayerName(domain.getPlayerName());
        player.setWeight(domain.getWeight());
        player.setHeight(domain.getHeight());
        if (null != domain.getGamePerformance()) {
            player.setGamePerformance(JacksonUtil.bean2Json(domain.getGamePerformance()));
        }
        String updator = domain.getMaintainInfo().getUpdator();
        Date updateTime = domain.getMaintainInfo().getUpdateTime();
        player.setUpdator(updator);
        player.setUpdateTime(updateTime);
        return player;
    }

    // domain -> event
    public PlayerUpdateEvent convertUpdateEvent(PlayerUpdateDomain domain) {
        PlayerUpdateEvent event = new PlayerUpdateEvent();
        event.setPlayerUpdateDomain(domain);
        event.setMessageId(UUID.randomUUID().toString());
        event.setMessageId(PlayerMessageType.UPDATE.getMsg());
        return event;
    }
}

```
## 2.5 intergration

本项目可能会依赖外部服务，那么将外部DTO转换为本项目可以理解的对象，需要在本层处理。

  

### 2.5.1 项目结构

假设本项目调用了用户中心服务：

xml

复制代码
```xml
user-demo-service-intergration
    -/src/main/java
        -user
            -adapter
                -UserClientAdapter.java
            -proxy
                -UserClientProxy.java
```
### 2.5.2 本项目间依赖关系

intergration依赖本项目两个模块：

- util
- domain

之所以依赖domain模块，是因为本层需要将外部DTO转换为本项目可以理解的对象，这些对象就放在domain模块。

text

复制代码
```xml
<dependency>
    <groupId>com.test.javafront</groupId>
    <artifactId>user-demo-service-domain</artifactId>
</dependency>
<dependency>
    <groupId>com.test.javafront</groupId>
    <artifactId>user-demo-service-util</artifactId>
</dependency>

```
### 2.5.3 核心代码

现在我们将外部对象UserClientDTO

转换为本项目领域对象UserInfoDomain

  

#### (1) 外部服务

```java
// 外部对象
public class UserInfoClientDTO implements Serializable {
    private String id;
    private String name;
    private Date createTime;
    private Date updateTime;
    private String mobile;
    private String cityCode;
    private String addressDetail;
}

// 外部服务
public class UserClientService {

    // RPC模拟
    public UserInfoClientDTO getUserInfo(String userId) {
        UserInfoClientDTO userInfo = new UserInfoClientDTO();
        userInfo.setId(userId);
        userInfo.setName(userId);
        userInfo.setCreateTime(DateUtil.now());
        userInfo.setUpdateTime(DateUtil.now());
        userInfo.setMobile("test-mobile");
        userInfo.setCityCode("test-city-code");
        userInfo.setAddressDetail("test-address-detail");
        return userInfo;
    }
}

```

  

#### (2) 本项目领域对象

domain模块新增user领域：
```xml
user-demo-service-domain
    -/src/main/java
        -user
            -domain
                -UserDomain.java
            -vo
                -UserAddressVO.java
                -UserContactVO.java

```

user领域对象代码：

```java
// 用户领域
public class UserInfoDomain extends BaseDomain {
    private UserContactVO contactInfo;
    private UserAddressVO addressInfo;
}

// 地址值对象
public class UserAddressVO extends BaseVO {
    private String cityCode;
    private String addressDetail;
}

// 联系方式值对象
public class UserContactVO extends BaseVO {
    private String mobile;
}

```

  

#### (3) 适配器

```java
public class UserClientAdapter {

    // third dto -> domain
    public UserInfoDomain convertUserDomain(UserInfoClientDTO userInfo) {
        UserInfoDomain userDomain = new UserInfoDomain();
        UserContactVO contactVO = new UserContactVO();
        contactVO.setMobile(userInfo.getMobile());
        userDomain.setContactInfo(contactVO);

        UserAddressVO addressVO = new UserAddressVO();
        addressVO.setCityCode(userInfo.getCityCode());
        addressVO.setAddressDetail(userInfo.getAddressDetail());
        userDomain.setAddressInfo(addressVO);
        return userDomain;
    }
}

```
#### (4) 调用外部服务

```java
public class UserClientProxy {

    @Resource
    private UserClientService userClientService;
    @Resource
    private UserClientAdapter userClientAdapter;

    public UserInfoDomain getUserInfo(String userId) {
        UserInfoClientDTO user = userClientService.getUserInfo(userId);
        UserInfoDomain result = userClientAdapter.convertUserDomain(user);
        return result;
    }
}

```

  

## 2.6 facade + client

设计模式中有一种Facade模式，称为门面模式或者外观模式。这种模式提供一个简洁对外语义，屏蔽内部系统复杂性。

client承载数据对外传输对象DTO，facade承载对外服务，这两层必须满足最小知识原则，无关信息不必对外透出。

这样做有两个优点：

- 简洁性：对外服务语义明确简洁
- 安全性：敏感字段不能对外透出

  

### 2.6.1 项目结构

#### (1) client

```xml
user-demo-service-client
    -/src/main/java
        -base
            -dto
                -BaseDTO.java
            -error
                -BizException.java
                -BizErrorCode.java
            -event
                -BaseEventDTO.java
            -result
                -ResultDTO.java
        -player
            -dto
                -PlayerCreateDTO.java
                -PlayerQueryResultDTO.java
                -PlayerUpdateDTO.java
            -enums
                -PlayerMessageTypeEnum.java
            -event
                -PlayerUpdateEventDTO.java
            -service
                -PlayerClientService.java

```
#### (2) facade
```xml
user-demo-service-facade
    -/src/main/java
        -player
            -adapter
                -PlayerFacadeAdapter.java
            -impl
                -PlayerClientServiceImpl.java
        -game
            -adapter
                -GameFacadeAdapter.java
            -impl
                -GameClientServiceImpl.java

```
### 2.6.2 本项目间依赖关系

client不依赖本项目其它模块，这一点非常重要，因为client会被外部引用，必须保证这一层简洁和安全。

facade依赖本项目三个模块：

- domain
- client
- service

text

复制代码
```xml
<dependency>
    <groupId>com.test.javafront</groupId>
    <artifactId>user-demo-service-domain</artifactId>
</dependency>
<dependency>
    <groupId>com.test.javafront</groupId>
    <artifactId>user-demo-service-client</artifactId>
</dependency>
<dependency>
    <groupId>com.test.javafront</groupId>
    <artifactId>user-demo-service-service</artifactId>
</dependency>

```
### 2.6.3 核心代码

#### (1) DTO

以查询运动员信息为例，查询结果DTO只封装最关键字段，例如运动员ID、创建时间、修改时间等业务不强字段就无须透出：

java

复制代码
```java
public class PlayerQueryResultDTO implements Serializable {
    private String playerName;
    private Integer height;
    private Integer weight;
    private GamePerformanceDTO gamePerformanceDTO;
}

```
#### (2) 客户端服务
```java
public interface PlayerClientService {
    public ResultDTO<PlayerQueryResultDTO> queryById(String playerId);
}

```
#### (3) 适配器

```java
public class PlayerFacadeAdapter {

    // domain -> dto
    public PlayerQueryResultDTO convertQuery(PlayerQueryResultDomain domain) {
        if (null == domain) {
            return null;
        }
        PlayerQueryResultDTO result = new PlayerQueryResultDTO();
        result.setPlayerId(domain.getPlayerId());
        result.setPlayerName(domain.getPlayerName());
        result.setHeight(domain.getHeight());
        result.setWeight(domain.getWeight());
        if (null != domain.getGamePerformance()) {
            GamePerformanceDTO performance = convertGamePerformance(domain.getGamePerformance());
            result.setGamePerformanceDTO(performance);
        }
        return result;
    }
}

```
#### (4) 服务实现

```java
public class PlayerClientServiceImpl implements PlayerClientService {

    @Resource
    private PlayerService playerService;
    @Resource
    private PlayerFacadeAdapter playerFacadeAdapter;

    @Override
    public ResultDTO<PlayerQueryResultDTO> queryById(String playerId) {
        PlayerQueryResultDomain resultDomain = playerService.queryPlayerById(playerId);
        if (null == resultDomain) {
            return ResultCommonDTO.success();
        }
        PlayerQueryResultDTO result = playerFacadeAdapter.convertQuery(resultDomain);
        return ResultCommonDTO.success(result);
    }
}

```


## 2.7 controller

facade服务实现可以作为RPC提供服务，controller则作为本项目HTTP接口提供服务，供前端调用。

controller需要注意HTTP相关特性，敏感信息例如登陆用户ID不能依赖前端传递，登陆后前端会在请求头带一个登陆用户信息，服务端需要从请求头中获取并解析。

  

### 2.7.1 项目结构


```xml
user-demo-service-controller
    -/src/main/java
        -config
            -CharsetConfig.java
        -controller
            -player
                -PlayerController.java
            -game
                -GameController.java
```

### 2.7.2 本项目依赖关系

controller依赖本项目一个模块：

- facade

根据依赖传递原理同时依赖以下模块：

- domain
- client
- service

text

复制代码

```xml
<dependency>
    <groupId>com.test.javafront</groupId>
    <artifactId>user-demo-service-facade</artifactId>
</dependency>

```


### 2.7.3 核心代码

```java
@RestController
@RequestMapping("/player")
public class PlayerController {

    @Resource
    private PlayerClientService playerClientService;

    @PostMapping("/add")
    public ResultDTO<Boolean> add(@RequestHeader("test-login-info") String loginUserId, @RequestBody PlayerCreateDTO dto) {
        dto.setCreator(loginUserId);
        ResultCommonDTO<Boolean> resultDTO = playerClientService.addPlayer(dto);
        return resultDTO;
    }

    @PostMapping("/update")
    public ResultDTO<Boolean> update(@RequestHeader("test-login-info") String loginUserId, @RequestBody PlayerUpdateDTO dto) {
        dto.setUpdator(loginUserId);
        ResultCommonDTO<Boolean> resultDTO = playerClientService.updatePlayer(dto);
        return resultDTO;
    }

    @GetMapping("/{playerId}/query")
    public ResultDTO<PlayerQueryResultDTO> queryById(@RequestHeader("test-login-info") String loginUserId, @PathVariable("playerId") String playerId) {
        ResultCommonDTO<PlayerQueryResultDTO> resultDTO = playerClientService.queryById(playerId);
        return resultDTO;
    }
}

```
## 2.8 boot

boot作为启动层，只有启动入口代码

  

### 2.8.1 项目结构

所有模块代码均必须属于com.user.demo.service子路径

user-demo-service-boot
    -/src/main/java
        -com.user.demo.service
            -MainApplication.java




### 2.8.2 本项目间依赖

boot引用本项目所有模块

- util
- integration
- infrastructure
- service
- domain
- facade
- controller
- client

  

### 2.8.3 核心代码

```java
@MapperScan("com.user.demo.service.infrastructure.*.mapper")
@SpringBootApplication
public class MainApplication {
    public static void main(final String[] args) {
        SpringApplication.run(MainApplication.class, args);
    }
}

```

  

# 3 文章总结

我们再次回顾分层五个思考维度：

#### (1) 单一

每层只处理一类事情，例如util只承载工具对象，integration只处理外部服务，每层职责单一且清晰

#### (2) 降噪

如无必要无增实体，例如查询结果DTO只透出最关键字段，例如运动员ID、创建时间、修改时间等业务不强字段无须透出

#### (3) 适配

service、facade、intergration层都存在适配器，翻译信息为本层或者下层可以理解的信息

#### (4) 业务

业务对象可以通过充血模型聚合业务，例如在业务对象中聚合业务校验逻辑

#### (5) 数据

数据对象要纯净，例如通过string类型保存比赛表现，数据层无需解析

  

  
