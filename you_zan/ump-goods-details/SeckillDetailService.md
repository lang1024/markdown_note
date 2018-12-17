###SeckillDetailService 详情页秒杀信息服务

```java
   /**
     * 微页面获取秒杀活动列表
     * @param queryParams
     * @return
     */
    PlainResult<List<DetailSeckill>> getSeckillList(QueryParams queryParams);

    /**
     * 获取秒杀预约数
     */
    PlainResult<Integer> getBookingNum(Long kdtId, Long seckillId);
```



####1.getSeckillList

##### 1.1参数 QueryParams

```java
 long kdtId;

    /**
     * 查询秒杀活动id列表
     */
    List<Integer> seckillIds;

    /**
     * 是否隐藏售罄的活动商品
     */
    boolean hideGoodsSold;

    /**
     * 是否隐藏已经结束的活动商品
     */
    boolean hideGoodsEnd;

    /**
     * 隐藏已经结束的活动商品的方式：
     * 0: 隐藏结束时间超过24小时的活动；
     * 1: 隐藏全部已经结束的活动
     */
    int goodsEndType;
```

##### 1.2出参 List<DetailSeckill>

DetailSeckill

```java
 	/**
     * 活动id
     */
    private int id;

    private long kdtId;

    /**
     * 商品Id
     */
    private int goodsId;

    /**
     * 活动状态
     * 0:未开始; 1:进行中; 2:其他
     */
    private int status;

    /**
     * 是否开启秒杀资格设置
     * 0: 否; 1: 是
     */
    private int isCheckRight;

    /**
     * 是否要关注店铺，完成预约
     * 0: 不要; 1: 要
     */
    private int useFollow;

    /**
     * 是否要回答问题正确，完成预约
     * 0: 不要; 1: 要
     */
    private int useQuestion;

    /**
     * 回答问题来完成预约的问题ID
     */
    private long questionId;

    /**
     * 活动开始时间戳
     */
    private int beginAt;

    /**
     * 活动结束时间戳
     */
    private int endAt;

    /**
     * 服务器产生的当前时间戳，给前端同步时间用
     */
    private int current;

    /**
     * 活动别名
     */
    private String activityAlias;

    /**
     * 秒杀页详细链接
     */
    private String detailUrl;

    /**
     * 秒杀活动冻结的库存量
     */
    private int frozenStock;

    /**
     * 秒杀活动当前的库存量
     */
    private int currentStock;

    /**
     * 活动总库存量
     */
    private int activityStock;

    /**
     * 预约数量
     */
    private int bookingNum;

    /**
     * 活动标签
     */
    private String tag;

    /**
     * 是否已经删除
     * 0: 未删除; 1: 已删除
     */
    private int isDelete;

    /**
     * 活动商品设置的sku信息
     */
    List<SkuInfo> skuInfos;
```

skuInfo

```java
 /**
     * 商品skuId
     */
    private long skuId;

    /**
     * 秒杀价格
     */
    private long seckillPrice;
```

#####1.3流程

![](https://ws1.sinaimg.cn/large/bd9c8deely1fy8nmnnwklj20tk118n35.jpg)