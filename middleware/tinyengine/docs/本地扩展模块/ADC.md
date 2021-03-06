## #ADC API


<div class="bi-table">
  <table>
    <colgroup>
      <col width="90px" />
      <col width="90px" />
    </colgroup>
    <tbody>
      <tr>
        <td rowspan="1" colSpan="1">
          <div data-type="p">API</div>
        </td>
        <td rowspan="1" colSpan="1">
          <div data-type="p">说明</div>
        </td>
      </tr>
      <tr height="34px">
        <td rowspan="1" colSpan="1">
          <div data-type="p"></div>
        </td>
        <td rowspan="1" colSpan="1">
          <div data-type="p"></div>
        </td>
      </tr>
      <tr>
        <td rowspan="1" colSpan="1">
          <div data-type="p">ADC.open(id)</div>
        </td>
        <td rowspan="1" colSpan="1">
          <div data-type="p"><span data-type="color" style="color:#F5222D">功能：</span>配置和启动adc</div>
          <div data-type="p"><span data-type="color" style="color:#F5222D">参数：</span> id:和板级配置文件中的id保持一致； </div>
          <div data-type="p"><span data-type="color" style="color:#F5222D">返回值：</span>成功：回资源handle，失败:-1</div>
        </td>
      </tr>
      <tr>
        <td rowspan="1" colSpan="1">
          <div data-type="p">ADC.read(handle)</div>
        </td>
        <td rowspan="1" colSpan="1">
          <div data-type="p"><span data-type="color" style="color:#F5222D">功能：</span>获取当前adc值 </div>
          <div data-type="p"><span data-type="color" style="color:#F5222D">参数：</span>handle:资源handle，为ADC.open的返回值;</div>
          <div data-type="p"><span data-type="color" style="color:#F5222D">返回值：</span>adc值</div>
        </td>
      </tr>
      <tr height="34px">
        <td rowspan="1" colSpan="1">
          <div data-type="p">ADC.close(handle)</div>
        </td>
        <td rowspan="1" colSpan="1">
          <div data-type="p"><span data-type="color" style="color:#F5222D">功能：</span>关闭adc </div>
          <div data-type="p"><span data-type="color" style="color:#F5222D">参数：</span>handle:资源handle，为ADC.open的返回值; </div>
          <div data-type="p">
            <span data-type="color" style="color:#F5222D">返回值：</span>0=ok other=fail;</div>
        </td>
      </tr>
    </tbody>
  </table>
</div>


## #板级配置参数


<div class="bi-table">  <table>    <colgroup>      <col width="90px" />      <col width="90px" />      <col width="90px" />    </colgroup>    <tbody>      <tr height="34px">        <td rowspan="1" colSpan="1">          <div data-type="p"><span data-type="color" style="color:rgb(38, 38, 38)"><span data-type="background" style="background-color:rgb(250, 250, 250)">参数名</span></span>          </div>        </td>        <td rowspan="1" colSpan="1">          <div data-type="p">类型/功能/值</div>        </td>        <td rowspan="1" colSpan="1">          <div data-type="p">说明</div>        </td>      </tr>      <tr height="34px">        <td rowspan="1" colSpan="1">          <div data-type="p">&quot;id&quot;</div>        </td>        <td rowspan="1" colSpan="1">          <div data-type="p"><span data-type="color" style="color:#F5222D">功能：</span>资源唯一性标志; </div>          <div data-type="p"><span data-type="color" style="color:#F5222D">类型：</span>string </div>          <div data-type="p">            <span data-type="color" style="color:#F5222D">值：</span>任意，保持数组内id值唯一;</div>        </td>        <td rowspan="1" colSpan="1">          <div data-type="p">该id值和js层GPIO.open时的id值保持一致;</div>        </td>      </tr>      <tr height="34px">        <td rowspan="1" colSpan="1">          <div data-type="p">&quot;port&quot;</div>        </td>        <td rowspan="1" colSpan="1">          <div data-type="p"><span data-type="color" style="color:#F5222D">功能：</span>端口值; </div>          <div data-type="p">            <span data-type="color" style="color:#F5222D">类型：</span>number </div>          <div data-type="p">            <span data-type="color" style="color:#F5222D">值：</span>和板级资源描述保持一致；</div>        </td>        <td rowspan="1" colSpan="1">          <div data-type="p">该port值和HAL层API对应的port保持一致；</div>        </td>      </tr>      <tr height="34px">        <td rowspan="1" colSpan="1">          <div data-type="p">&quot;sampling&quot;</div>        </td>        <td rowspan="1" colSpan="1">          <div data-type="p"><span data-type="color" style="color:#F5222D">功能：</span>采样频率; </div>          <div data-type="p"><span data-type="color" style="color:#F5222D">类型：</span>number </div>          <div data-type="p"><span data-type="color" style="color:#F5222D">值：</span>依据实际情况进行配置；</div>        </td>        <td rowspan="1" colSpan="1">          <div data-type="p"></div>        </td>      </tr>    </tbody>  </table></div>



## #板级配置示范
```json
/*apps/js/board_config.json*/
{

	"ADC":[
		{
		"id":"light",
		"port":34,
		"sampling":12000000
		}
	]

}
```


## #ESP32之光敏模块

### #硬件
1)esp32Kit开发板
2)光敏模块


![1.png | left | 412x404](https://cdn.yuque.com/lark/0/2018/png/66207/1525858906149-846cdf85-fec3-45b6-8de5-a488b05fe535.png "")

### #接线

EPS32 IO34引脚 连接 按键模块的OUT引脚；
EPS32 GND引脚 连接 按键模块的GND引脚；
EPS32 3.3V引脚 连接 按键模块的VCC引脚；

### #配置
```json
/*apps/js/board_config.json*/
{

	"ADC":[
		{
		"id":"light",
		"port":34,
		"sampling":12000000
		}
	]

}
```

### #代码
```javascript
var light_handle = ADC.open('light');
setInterval(function(){
	var i = 0;
	var LigthValue = 0;
	for(i=0;i<10;i++){
		LigthValue += ADC.read(light_handle);
	}
	LigthValue = LigthValue/10;
	if(LigthValue > 4500){
		LigthValue = 4500;
	}
	LigthValue = 100 - LigthValue/45;
	console.log('LigthValue:'+LigthValue);
},5000);
```

### #现象
光敏范围：0-100，越大代表亮度越强。


![1.png | left | 313x265](https://cdn.yuque.com/lark/0/2018/png/66207/1525859077287-755e0f76-3266-409b-842b-84ce3fdc6198.png "")



## #TODO


 