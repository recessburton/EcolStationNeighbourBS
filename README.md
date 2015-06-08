Author:YTC 
Mail:recessburton@gmail.com
Created Time: 2015.6.4

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>

Description：
	Telosb 上层模拟实现的ORW邻居关系建立过程基站接口.
	每个节点各自发送hello包，接收其它节点回复的ack包，计算“链路质量”，
	据此排序选择邻居加入邻居set.
	周期性地通过CTP向根节点发送节点的邻居集.
	基站接收CTP包并通过UART发送至PC.
	仅需调用本接口命令startNei()即可，触发时间neighbourDone()事件，
	返回可直接用于UART发送的uint8_t邻居数据包.
	
Logs：
	V 0.3 将UART发送功能去除，改成事件的形式返回邻居节点数据包，解决了
	调用本接口的组件也包含UART时引起的冲突问题
	V 0.2 更正Bug #1,将根节点节点号默认设置成1
	V 0.1 完成基本功能
	
Known Bugs: 
	#1: 各节点不以基站（0号）做邻居。

