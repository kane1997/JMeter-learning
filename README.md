# Jmeter

# 下载：

<aside>
💡 需要预先配置java 8 环境<环境配置略>

</aside>

### [官方下载地址]

[Download Apache JMeter](https://jmeter.apache.org/download_jmeter.cgi)

<aside>
💡 下载完成后需要解压zip包，打开文件

**Windows用户运行\bin\jmeter.bat文件
MAC用户运行\bin\jmeter**

</aside>

---

# **Jmeter性能参数配置**

- 线程数:一个用户占一个线程，200个线程就是模拟200个用户;
- Ramp-Up Period(in seconds):设置线程需要多长时间全部启动。如果线程数为200 ，准备时长为10 ，那么*
- 需要1秒钟启动20个线程。也就是每秒钟启动20个线程;
- 循环次数:每个线程发送请求的次数。如果线程数为200，循环次数为10，那么每个线程发送10次请求。总Samples为200*10=2000。如果勾选了“永远”，那么所有线程会一直发送请求，直到选择停止运行脚本。

注意，如果要真正模拟多个用户并发的话，比如说你要模拟100个用户并发，那么你的线程数一定得是100，不能是25个线程，每个线程 内包含4个请求，举个栗子，假如有4个接口，要模拟2000个用户并发，每个接口500个用户，那么你的解决方案是：建立4个线程组，每个线程组的线程数是500，同时并发运行4个线程组（这一点你不用做，jmeter的机制 就是线程组都是并发运行的，不用担心这个）

- Summary Report参数解释
- Samples:发送了多少个请求;
- Average:平均请求时间;
- Min:最小请求时间;
- Max:最大请求时间;
- Error:请求失败率;
- Throughput:Throughput，即每秒钟服务器处理的Samples，单位是tps(transaction per second)，也有说成是* rps(request per second); Utilibill说的是hps（hit per second)
- KB/sec:服务器每秒接收的数据量;
- 90% Line:90%请求响应时间不会超过XX秒;
- Median:中位数，50%响应时间小于XX秒;
    
    ![  **Figure 1: Jmeter测试界面**](Jmeter%20d7cf7/%E6%88%AA%E5%B1%8F2022-03-31_04.04.45.png)
    
      **Figure 1: Jmeter测试界面**
    
    ---
    
    ## 创建流程:
    
    ### STEP 1: 创建线程组
    
    <aside>
    💡 PATH: Test Plan→Add→Threads(Users)→Thread Group
    
    </aside>
    
    ![**Figure 2：创建线程组流程**](Jmeter%20d7cf7/%E6%88%AA%E5%B1%8F2022-03-31_04.05.31.png)
    
    **Figure 2：创建线程组流程**
    
    ---
    
    ### STEP 2 :设置压力测试等级
    
    <aside>
    💡 设置线程数量，每秒流量进入时间（流向控制），设置循环次数
    
    </aside>
    
    ![**Figure 3:设置线程组参数**](Jmeter%20d7cf7/%E6%88%AA%E5%B1%8F2022-03-31_10.13.40.png)
    
    **Figure 3:设置线程组参数**
    
    ---
    
    ### STEP3:设置请求默认值，这里为储存host访问位置
    
    <aside>
    💡 PATH:添加→配置原件→HTTP请求默认值
    
    </aside>
    
    ![Figure 4:设置请求默认值](Jmeter%20d7cf7/%E6%88%AA%E5%B1%8F2022-03-31_10.29.44.png)
    
    Figure 4:设置请求默认值
    
    <aside>
    💡 这里我们使用http协议，设置默认主机路径，**注意这里的服务器IP名称不包含https://**
    
    </aside>
    
    ![Figure 5:输入Web服务器端信息](Jmeter%20d7cf7/%E6%88%AA%E5%B1%8F2022-03-31_10.32.11.png)
    
    Figure 5:输入Web服务器端信息
    
    ---
    
    ### STEP 4 :添加任务，这里是添加HTTP请求,设置监听器
    
    <aside>
    💡 PATH:HTTP请求→Add→Listener→Summary Report/Aggregation Report/View result tree(汇总报告、聚合报告、查看结果树)
    
    </aside>
    
    ![**Figure 6: Step 2 展示流程**](Jmeter%20d7cf7/%E6%88%AA%E5%B1%8F2022-03-31_09.58.38.png)
    
    **Figure 6: Step 2 展示流程**
    
    ---
    
    ### STEP 5:建立脚本
    
    <aside>
    💡 **对HTTP请求设置路径，协议选择HTTP，服务器和IP输入待测web路径，选择HTTP请求类型，设置web中的操作路径**
    
    </aside>
    
    ![**Figure 7:对HTTP设置脚本**](Jmeter%20d7cf7/%E6%88%AA%E5%B1%8F2022-03-31_10.20.22.png)
    
    **Figure 7:对HTTP设置脚本**
    
    ---
    
    ### STEP 6:点击运行，查看参数
    
    <aside>
    💡 **从每一个监听器中可以查看当前运行时测试的数据完成情况，和相关参数**
    
    </aside>
    
    ![**Figure 8: 查看结果树相关参数**](Jmeter%20d7cf7/%E6%88%AA%E5%B1%8F2022-03-31_04.06.28.png)
    
    **Figure 8: 查看结果树相关参数**
    
    ---