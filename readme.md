# 基于JavaScript开发的房贷计算器

房贷计算器可以帮助估算每月的还款金额以及其他与按揭相关的财务费用。它还提供了几个选项，可以将额外的付款或者常见的抵押贷款相关费用的年增长率考虑在内。

## 预览地址

https://fangdai.gitapp.cn

## 关键源码

```
    <div class="container">
        <div class="calculator">
            <div view="calc_input" style="display:block;">
                <div class="ui-bar" skin="title">
                    <at class="title">
                        房贷计算器
                    </at>
                </div>
                <nav class="switch-tabs big-switch-tabs">
                    <ul style="cursor: pointer;">
                        <li id="business_calc" class="tab select-tab">
                            <div>商业贷款</div>
                        </li>
                        <li id="PAF_calc" class="tab normal-tab">
                            <div>公积金贷款</div>
                        </li>
                        <li id="mix_calc" class="tab normal-tab">
                            <div>组合贷款</div>
                        </li>
                    </ul>
                </nav>
                <div class="input-fields" wrap="h10">
                    <ul>
                        <li id="business_sum_line" class="field-wrap">
                            <label>商业贷款</label>
                            <div class="field">
                                <div class="ui-text" data-tail="万元">
                                    <input type="number" id="business_sum" value="100">
                                </div>
                            </div>
                        </li>
                        <li id="PAF_sum_line" class="field-wrap" style="display:none">
                            <label>公积金贷款</label>
                            <div class="field">
                                <div class="ui-text" data-tail="万元">
                                    <input type="number" id="PAF_sum" value="80">
                                </div>
                            </div>
                        </li>
                        <li class="field-wrap">
                            <label>贷款期限</label>
                            <div class="field">
                                <div class="ui-select">
                                    <div class="value-bar">
                                        <span id="loan_period_select_bar" class="text" value="20">20年（240期）</span>
                                        <span class="icon-sps tail-icon"></span>
                                    </div>
                                    <select id="loan_period_select">
                                        <option value="0">半年（6期）</option>
                                        <option value="1">1年（12期）</option>
                                        <option value="2">2年（24期）</option>
                                        <option value="3">3年（36期）</option>
                                        <option value="4">4年（48期）</option>
                                        <option value="5">5年（60期）</option>
                                        <option value="6">6年（72期）</option>
                                        <option value="7">7年（84期）</option>
                                        <option value="8">8年（96期）</option>
                                        <option value="9">9年（108期）</option>
                                        <option value="10">10年（120期）</option>
                                        <option value="11">11年（132期）</option>
                                        <option value="12">12年（144期）</option>
                                        <option value="13">13年（156期）</option>
                                        <option value="14">14年（168期）</option>
                                        <option value="15">15年（180期）</option>
                                        <option value="16">16年（192期）</option>
                                        <option value="17">17年（204期）</option>
                                        <option value="18">18年（216期）</option>
                                        <option value="19">19年（228期）</option>
                                        <option value="20" selected="selected">20年（240期）</option>
                                        <option value="21">21年（252期）</option>
                                        <option value="22">22年（264期）</option>
                                        <option value="23">23年（276期）</option>
                                        <option value="24">24年（288期）</option>
                                        <option value="25">25年（300期）</option>
                                        <option value="26">26年（312期）</option>
                                        <option value="27">27年（324期）</option>
                                        <option value="28">28年（336期）</option>
                                        <option value="29">29年（348期）</option>
                                        <option value="30">30年（360期）</option>
                                    </select>
                                </div>
                            </div>
                        </li>
                        <li id="business_rate_select_line" class="field-wrap">
                            <label>商贷利率</label>
                            <div class="field long-field" id="business_rate_select_field">
                                <div class="ui-select">
                                    <div class="value-bar">
                                        <span id="business_rate_select_bar" class="text" value="12">最新基准利率</span>
                                        <span class="icon-sps tail-icon"></span>
                                    </div>
                                    <select id="business_rate_select" input-method="auto">
                                        <option value="-1">手动输入</option>
                                        <option value="12" data-key="18-1-1" selected="selected">最新基准利率</option>
                                    </select>
                                </div>
                            </div>
                            <div class="field short-field" id="business_discount_field">
                                <div class="ui-select">
                                    <div class="value-bar">
                                        <span id="business_discount_bar" class="text" data-discount="1.0">无折扣</span>
                                        <span class="icon-sps tail-icon"></span>
                                    </div>
                                    <select id="business_discount">
                                        <option value="0" data-discount="1.0" selected="selected">无折扣</option>
                                        <option value="10" data-discount="1.2">1.2倍</option>
                                        <option value="9" data-discount="1.15">1.15倍</option>
                                        <option value="8" data-discount="1.1">1.1倍</option>
                                        <option value="7" data-discount="1.05">1.05倍</option>
                                        <option value="6" data-discount="0.95">95折</option>
                                        <option value="5" data-discount="0.9">9折</option>
                                        <option value="4" data-discount="0.85">85折</option>
                                        <option value="3" data-discount="0.8">8折</option>
                                        <option value="2" data-discount="0.75">75折</option>
                                        <option value="1" data-discount="0.7">7折</option>
                                    </select>
                                </div>
                            </div>
                        </li>
                        <li id="business_rate_value_line" class="field-wrap">
                            <label></label>
                            <div class="field">
                                <div class="ui-text rate-text" data-tail="%">
                                    <input type="number" id="business_rate" value="4.2">
                                </div>
                            </div>
                        </li>
                        <li id="PAF_rate_line" class="field-wrap" style="display:none">
                            <label>公积金利率</label>
                            <div class="field long-field">
                                <div class="ui-select">
                                    <div class="value-bar">
                                        <span id="PAF_rate_select_bar" class="text" value="12">最新基准利率</span>
                                        <span class="icon-sps tail-icon"></span>
                                    </div>
                                    <select id="PAF_rate_select" input-method="auto">
                                        <option value="-1">手动输入</option>
                                        <option value="12" data-key="18-1-1" selected="selected">最新基准利率</option>
                                    </select>
                                </div>
                            </div>
                            <div class="field short-field">
                                <div class="ui-text" data-tail="%">
                                    <input type="number" id="PAF_rate" value="3.25">
                                </div>
                            </div>
                        </li>
                        <li class="field-wrap">
                            <label>还款方式</label>
                            <div class="field mid-field">
                                <label class="repay-method">
                                    <input type="radio" name="repayType" id="repay_radio1" value="1"
                                        checked="checked">&nbsp;等额本息</label>
                            </div>
                            <div class="field mid-field">
                                <label class="repay-method">
                                    <input type="radio" name="repayType" id="repay_radio2" value="2">&nbsp;等额本金</label>
                            </div>
                        </li>
                    </ul>
                    <div class="calbtn-wrap">
                        <a id="calculate" class="ui-btn" skin="blue full">计&nbsp;算</a>
                    </div>
                </div>
                <div wrap="t15">
                    <div class="use-help">

                    </div>

                </div>
            </div>
            <div class="calc-result hide" view="calc_result">
                <header class="ui-bar" skin="title">
                    <div class="title">计算结果</div>
                    <div class="left">
                        <a id="back_to_calc_input" class="ui-btn" skin="mini back" wrap="t5">返回</a>
                    </div>
                </header>
                <nav class="switch-tabs">
                    <ul>
                        <li id="result_tab_1" class="result-tab normal-tab" tab-id="1">
                            <div style="cursor:pointer;">等额本息</div>
                        </li>
                        <li id="result_tab_2" class="result-tab normal-tab" tab-id="2">
                            <div style="cursor: pointer;">等额本金</div>
                        </li>
                    </ul>
                </nav>
                <div id="result_data_1" class="result-data hide">
                    <ul class="result-list">
                        <li class="group-tit">还款数据摘要</li>
                        <li id="business_interest_total_debx" class="hide">
                            <div class="item-name">商贷利息</div>
                            <div id="business_interest_total_1" class="item-value"></div>
                        </li>
                        <li id="PAF_interest_total_debx" class="hide">
                            <div class="item-name">公积金利息</div>
                            <div id="PAF_interest_total_1" class="item-value"></div>
                        </li>
                        <li>
                            <div class="item-name">利息总额</div>
                            <div id="interest_total_1" class="item-value"></div>
                        </li>
                        <li>
                            <div class="item-name">累计还款总额</div>
                            <div id="repay_total_1" class="item-value"></div>
                        </li>
                        <li>
                            <div class="item-name">每月月供</div>
                            <div id="repay_monthly_1" class="item-value"></div>
                        </li>
                        <li>
                            <div class="item-name">最高月付利息</div>
                            <div id="interest_monthly_1" class="item-value"></div>
                        </li>
                    </ul>
                    <div class="data-container wid2 clear">
                        <div class="group-tit">还款数据明细</div>
                        <table class="data-table table-striped">
                            <thead>
                                <tr>
                                    <th>期次</th>
                                    <th>偿还本息</th>
                                    <th>偿还利息</th>
                                    <th>偿还本金</th>
                                    <th>剩余本金</th>
                                </tr>
                            </thead>
                            <tbody id="simple_data_table_1"></tbody>
                        </table>
                        <div class="view-more" data-detail="1">
                            <div class="detail">
                                <p class="txt">查看更多数据...</p>
                            </div>
                            <i data-icon="&gt;"></i>
                        </div>
                    </div>
                </div>
                <div id="result_data_2" class="result-data hide">
                    <ul class="result-list">
                        <li class="group-tit">还款数据摘要</li>
                        <li id="business_interest_total_debj" class="hide">
                            <div class="item-name">商贷利息</div>
                            <div id="business_interest_total_2" class="item-value"></div>
                        </li>
                        <li id="PAF_interest_total_debj" class="hide">
                            <div class="item-name">公积金利息</div>
                            <div id="PAF_interest_total_2" class="item-value"></div>
                        </li>
                        <li>
                            <div class="item-name">利息总额</div>
                            <div id="interest_total_2" class="item-value"></div>
                        </li>
                        <li>
                            <div class="item-name">累计还款总额</div>
                            <div id="repay_total_2" class="item-value"></div>
                        </li>
                        <li>
                            <div class="item-name">最高月供</div>
                            <div id="repay_monthly_2" class="item-value"></div>
                        </li>
                        <li>
                            <div class="item-name">最高月付利息</div>
                            <div id="interest_monthly_2" class="item-value"></div>
                        </li>
                    </ul>
                    <div class="data-container wid2 clear">
                        <div class="group-tit">还款数据明细</div>
                        <table class="data-table table-striped">
                            <thead>
                                <tr>
                                    <th>期次</th>
                                    <th>偿还本息</th>
                                    <th>偿还利息</th>
                                    <th>偿还本金</th>
                                    <th>剩余本金</th>
                                </tr>
                            </thead>
                            <tbody id="simple_data_table_2"></tbody>
                        </table>
                        <div class="view-more" data-detail="2">
                            <div class="detail">
                                <p class="txt">查看更多数据...</p>
                            </div>
                            <i data-icon="&gt;"></i>
                        </div>
                    </div>
                </div>
                <div class="recal-btn" wrap="h10">
                    <a id="recalculate" class="ui-btn" skin="blue full">重新计算</a>
                </div>
                <div wrap="t15">
                    <div class="use-help">

                    </div>
                </div>
            </div>
            <div id="data_detail_bar" class="ui-bar-fixed hide">
                <header class="ui-bar" skin="title">
                    <div class="title">数据明细</div>
                    <div class="left">
                        <a id="back_to_calc_result" class="ui-btn" skin="mini back" wrap="t5">返回</a>
                    </div>
                </header>
            </div>
            <div class="data-detail hide" view="data_detail">
                <div id="data_detail_1" class="data-container wid2 clear hide">
                    <table class="data-table table-striped">
                        <thead>
                            <tr>
                                <th>期次</th>
                                <th>偿还本息</th>
                                <th>偿还利息</th>
                                <th>偿还本金</th>
                                <th>剩余本金</th>
                            </tr>
                        </thead>
                        <tbody id="standard_data_table_1"></tbody>
                    </table>
                </div>
                <div id="data_detail_2" class="data-container wid2 clear hide">
                    <table class="data-table table-striped">
                        <thead>
                            <tr>
                                <th>期次</th>
                                <th>偿还本息</th>
                                <th>偿还利息</th>
                                <th>偿还本金</th>
                                <th>剩余本金</th>
                            </tr>
                        </thead>
                        <tbody id="standard_data_table_2"></tbody>
                    </table>
                </div>
            </div>
        </div>


        <div class="meta-layout">
            <h1>房贷计算器</h1>
            <p>房贷计算器可以帮助估算每月的还款金额以及其他与按揭相关的财务费用。它还提供了几个选项，可以将额外的付款或者常见的抵押贷款相关费用的年增长率考虑在内。这个计算器主要适用于中国的居民。</p>
            <h2>计算器组成</h2>
            <p>贷款通常包括以下关键部分。这些也是贷款计算器的基本组成部分。</p>
            <ul>
                <li>
                    贷款额: 从贷方或银行借入的金额。在抵押贷款中，这相当于购买价格减去任何首付款。一个人可以借到的最高贷款额通常与家庭收入或负担能力有关。要估计可负担的金额，请使用我们的房屋负担能力计算器。
                </li>
                <li>
                    首付款:
                    购买的预付款，通常是总价的一定比例。这是由借款人支付的购买价格的一部分。通常情况下，抵押贷款机构希望借款人支付20%或更多的首付。在某些情况下，借款人的首付可能低至3%。如果借款人的首付款低于20%，他们将被要求支付私人抵押贷款保险(PMI)。借款人需要持有这种保险，直到贷款的剩余本金降至房屋原始购买价格的80%以下。一般的经验法则是，首付越高，利率越优惠，贷款越有可能被批准。
                </li>
                <li>
                    贷款期限: 贷款必须全部偿还的时间。大多数固定利率抵押贷款的期限是15年、20年或30年。较短的期限，如15年或20年，通常包括较低的利率。
                </li>
                <li>
                    利率: 贷款费用占借款成本的百分比。
                </li>
            </ul>
            <h2>常见问题</h2>
            <p>下面是关于房贷的常见问题</p>
            <ul>
                <li>
                    <p>等额本金和等额本息的区别？ </p>
                    <p>等额本息法重要的一个特点是每月的还款额相同，从本质上来说是本金所占比例逐月递增，利息所占比例逐月递减，月还款数不变，即在月供“本金与利息”的分配比例中，前半段时期所还的利息比例大、本金比例小，还款期限过半后逐步转为本金比例大、利息比例小。等额本金法的特点是每月的还款额不同，呈现逐月递减的状态；它是将贷款本金按还款的总月数均分，再加上上期剩余本金的利息，这样就形成月还款额，所以等额本金法头一个个月的还款额比较多，然后逐月减少，越还越少。
                    </p>
                </li>
                <li>
                    <p>什么情况下适合提前还款？ </p>
                    <p>自然是目前的利率环境。按照金融理论，提前还贷是贷方(银行)向借方(购房者)提供的一种以贷款市值为标的看涨期权，或者是对于利率的看跌期权。原则上，只要市场利率低于当初借款的合同利率，该期权就是in-the-money的。实际中当然要考虑其他因素，其中最重要的是提前还款的成本。市场利率下跌幅度越大，就越应该提前还款。
                    </p>
                </li>
                <li>
                    <p>为什么银行房贷跟算出来的差距这么多？ </p>
                    <p>银行是根据您的还款方式，比如等额本息，当本金减少的时候利率自然减少。 非银行金融机构，通常算法是本金减少利息没有少，所以您会发现区别很大。</p>
                </li>
                <li>
                    <p>银行存款利率是怎么计算的？ </p>
                    <p>存款利率指客户按照约定条件存入银行帐户的货币，一定时间内利息额同贷出金额即本金的利率。有活期利率和定期利率之分，有年/月/日利率之分。</p>
                </li>
                <li>
                    <p>房贷计算器可以在哪些城市使用？ </p>
                    <p>目前主要服务于上海、北京、深圳、厦门、广州、杭州、三亚、南京、苏州、天津、青岛等城市以及华东沿海地区。</p>
                </li>
            </ul>


        </div>

        <div id="share"></div>
        <div class="row recommend">
            <div class="recommend-head">知识库</div>
            <div class="recommend-list">
                <a class="recommend-list-item" href="https://fangdaijisuanqi.vip/fangdai/1001.html">2024年全国房价是涨还是跌</a>
                <a class="recommend-list-item" href="https://fangdaijisuanqi.vip/fangdai/1002.html">lpr浮动利率可以选吗</a>
                <a class="recommend-list-item" href="https://fangdaijisuanqi.vip/fangdai/1003.html">公积金贷款能贷多少</a>
                <a class="recommend-list-item" href="https://fangdaijisuanqi.vip/fangdai/1004.html">提前还房贷的最好时期</a>
                <a class="recommend-list-item" href="https://fangdaijisuanqi.vip/fangdai/1005.html">房贷还不上怎么办</a>
                <a class="recommend-list-item" href="https://fangdaijisuanqi.vip/fangdai/1006.html">lpr利率历史数据</a>
                <a class="recommend-list-item" href="https://fangdaijisuanqi.vip/fangdai/1007.html">一线城市或迎新一波楼市松绑</a>
                <a class="recommend-list-item" href="https://fangdaijisuanqi.vip/fangdai/1008.html">楼市2024年能否触底</a>
            </div>
        </div>
    </div>



```

## 参考资料

- https://fangdai.gitapp.cn
- https://sina.com
