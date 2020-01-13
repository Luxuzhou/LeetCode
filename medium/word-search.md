# **题目地址**
https://leetcode-cn.com/problems/word-search/
# **题目描述**
```
给定一个二维网格和一个单词，找出该单词是否存在于网格中。
单词必须按照字母顺序，通过相邻的单元格内的字母构成，其中“相邻”单元格是那些水平相邻或垂直相邻的单元格。同一个单元格内的字母不允许被重复使用。

示例:
board =
[
  ['A','B','C','E'],
  ['S','F','C','S'],
  ['A','D','E','E']
]

给定 word = "ABCCED", 返回 true.
给定 word = "SEE", 返回 true.
给定 word = "ABCB", 返回 false.
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def exist(self, board: List[List[str]], word: str) -> bool:
        row = len(board)
        col = len(board[0])
        def helper(i, j, k, visited):
            if k == len(word):
                return True
            for x, y in [(-1, 0), (1, 0), (0, 1), (0, -1)]:
                tmp_i = x + i
                tmp_j = y + j
                if 0 <= tmp_i < row and 0 <= tmp_j < col and (tmp_i, tmp_j) not in visited and board[tmp_i][tmp_j] == word[k]:
                    visited.add((tmp_i, tmp_j))
                    if helper(tmp_i, tmp_j, k + 1, visited):
                        return True
                    visited.remove((tmp_i, tmp_j))
            return False
        for i in range(row):
            for j in range(col):
                if board[i][j] == word[0] and helper(i, j, 1, {(i, j)}):
                    return True
        return False
```
C++ Code:
```
class Solution {
public:
    vector<vector<bool> > mark;
    int dir[4][2] = {{0, 1}, {1, 0}, {0, -1}, {-1, 0}};
    int m, n;
    vector<vector<char>> Board;
    string Word;
    bool dfs(int i, int j, int start) {
        if (Board[i][j] == Word[start]) {
            if (start == Word.length() - 1) return true;
            mark[i][j] = true;
            for(int k=0;k<4;k++) {
                int newx = i + dir[k][0];
                int newy = j + dir[k][1];
                if(newx >= 0 && newy >= 0 && newx < m && newy < n && mark[newx][newy] == false) {
                    if(dfs(newx,newy,start+1) ==true) return true;
                }
            }
            mark[i][j] = false;
        }
        return false;
    }
    
    bool exist(vector<vector<char>>& board, string word) {
        if (board.empty() || board[0].empty()) return false;
        m = board.size();
        n = board[0].size();
        for (int i = 0; i < m; i++) {
            vector<bool> t;
            for(int j = 0; j < n; j++) t.push_back(false);
            mark.push_back(t);
        }
        Board = board;
        Word = word;
        for(int i = 0; i < m; i++) {
            for(int j = 0; j < n; j++) {
                if(board[i][j] == word[0]) {
                    bool flag = dfs(i, j, 0);
                    if(flag == true) return flag;
                }
            }
        }
        return false;   
    }
};
```
