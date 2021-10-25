---
layout: post
title: cpp-maze
tag: cpp
---

# 回溯——迷宫
先看题：

> 一天蒜头君掉进了一个迷宫里面，蒜头君想逃出去，可怜的蒜头君连迷宫是否有能逃出去的路都不知道。（一堆废话）

> 第一行输入两个整数 nn 和 mm，表示这是一个 n \times mn×m 的迷宫。
>
>接下来的输入一个 nn 行 mm 列的迷宫。其中 ‘S’
表示蒜头君的位置，’*‘表示墙，蒜头君无法通过，’.‘表示路，蒜头君可以通过’.'移动，'T’表示迷宫的出口（蒜头君每次只能移动到四个与他相邻的位置——上，下，左，右）。
>
>输出格式 输出一个字符串，如果蒜头君可以逃出迷宫输出"yes"，否则输出"no"。
>
>数据范围
1≤n,m≤10。

回溯问题，很让人头疼，先看下回溯部分的伪代码：

``` javascript
void backtracking(参数) {
    if (终止条件) {
        存放结果;
        return;
    }

    for (选择：本层集合中元素（树中节点孩子的数量就是集合的大小）) {
        处理节点;
        backtracking(路径，选择列表); // 递归
        回溯，撤销处理结果
    }
}
```

用回溯函数是因为这里本来可以套for循环的，但是迷宫一大就要套十几层，CSP绝对超时。

看下完整代码：

``` javascript
#include<cstdio>
#include<iostream>
#include<algorithm>
#include<iomanip>
using namespace std;

int n, m, startX, startY;
char maze[50][50];
bool canSolve = false;
int nextX, nextY;
int ways[4][2] = {{0, -1}, {0, 1}, {-1, 0}, {1, 0}};  
int walked[50][50];

void solve(int nowX, int nowY, int step) {
	if (maze[nowX][nowY] == 'T') {
		//cout << "【slove/info】 " << nowX << " " << nowY << "At T!" << endl;
		canSolve = true;
		return;
	}
	else{
		//cout << "【slove/info】 nowX:" << nowX << " nowY:" << nowY << endl;
	}
	for (int tryWay = 0; tryWay < 4; tryWay++) {
		nextX += ways[tryWay][0];
		nextY += ways[tryWay][1];
		//cout << "【solve/info】 nextX:" << nextX << " nextY:" << nextY << endl;
		if (nextX >= 0 && nextY >= 0 && nextX < m && nextY < n && maze[nextX][nextY] != '*' && walked[nextX][nextY] == 0) {
			
			maze[nextX][nextY] = 'T';
			maze[nowX][nowY] = '.';
			walked[nextX][nextY] = step;
			nowX = nextX;
			nowY = nextY;
			solve(nowX, nowY, step+1);
		}
		else{
			//cout << "【solve/info】 nextX and nextY cannot move :(" << endl;
		}
		
		//cout << "【solve/info】 nextX:" << nextX << " nextY:" << nextY << "(in bottom of for)" << endl;
	}
}

int main() {
	freopen("maze.in", "r", stdin);
	freopen("maze.out", "w", stdout);
	cin >> n >> m;
	for (int y = 0; y < n; y++) {
		for (int x = 0; x < m; x++) {
			cin >> maze[x][y];
			if (maze[x][y] == 'S') {
				startX = x;
				startY = y;
			}
		}
	}
	solve(startX, startY, 0);
	if(canSolve)
		cout << "yes";
	else
		cout << "no";
	return 0;
}
```

不明白的看参考链接：
[题目及原答案--CSDN](https://blog.csdn.net/A793488316/article/details/104176651?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522163352566916780261936342%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=163352566916780261936342&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-12-104176651.pc_search_result_control_group&utm_term=%E7%AC%AC%E4%B8%80%E8%A1%8C%E8%BE%93%E5%85%A5%E4%B8%A4%E4%B8%AA%E6%95%B4%E6%95%B0+n+%E5%92%8C+m%EF%BC%8C%E8%A1%A8%E7%A4%BA%E8%BF%99%E6%98%AF%E4%B8%80%E4%B8%AAn%C3%97m+%E7%9A%84%E8%BF%B7%E5%AE%AB%E3%80%82+%E6%8E%A5%E4%B8%8B%E6%9D%A5%E7%9A%84%E8%BE%93%E5%85%A5%E4%B8%80%E4%B8%AA+n+%E8%A1%8C+m+%E5%88%97%E7%9A%84%E8%BF%B7%E5%AE%AB%E3%80%82%E5%85%B6%E4%B8%AD+%27S%27+%E8%A1%A8%E7%A4%BA%E5%B0%8F%E9%A3%9E%E7%9A%84%E4%BD%8D%E7%BD%AE%EF%BC%8C%27*%27%E8%A1%A8%E7%A4%BA%E5%A2%99%EF%BC%8C%E5%B0%8F%E9%A3%9E%E6%97%A0%E6%B3%95%E9%80%9A%E8%BF%87%EF%BC%8C%27.%27%E8%A1%A8%E7%A4%BA%E8%B7%AF%EF%BC%8C%E5%B0%8F%E9%A3%9E%E5%8F%AF%E4%BB%A5%E9%80%9A%E8%BF%87%27.%27%E7%A7%BB%E5%8A%A8%EF%BC%8C%27T%27%E8%A1%A8%E7%A4%BA%E8%BF%B7%E5%AE%AB%E7%9A%84%E5%87%BA%E5%8F%A3%EF%BC%88%E5%B0%8F%E9%A3%9E%E6%AF%8F%E6%AC%A1%E5%8F%AA%E8%83%BD%E7%A7%BB%E5%8A%A8%E5%88%B0%E5%9B%9B%E4%B8%AA%E4%B8%8E%E4%BB%96%E7%9B%B8%E9%82%BB%E7%9A%84%E4%BD%8D%E7%BD%AE%E2%80%94%E2%80%94%E4%B8%8A%EF%BC%8C%E4%B8%8B%EF%BC%8C%E5%B7%A6%EF%BC%8C%E5%8F%B3%EF%BC%89%E3%80%82&spm=1018.2226.3001.4187)
[讲解](https://programmercarl.com/%E5%9B%9E%E6%BA%AF%E7%AE%97%E6%B3%95%E7%90%86%E8%AE%BA%E5%9F%BA%E7%A1%80.html#%E5%85%B6%E4%BB%96%E8%AF%AD%E8%A8%80%E7%89%88%E6%9C%AC)
