##　プロジェクト名
三目並べ

### プロジェクト内容
三目並べゲーム(〇×三つ並べる)

## チーム名
tori

## チームメンバー
小田桐雅弥　加藤謙治

#include <iostream>
using namespace std;
char matrix[3][3] = {'1', '2', '3', '4', '5', '6', '7', '8', '9'};
char player = 'X';
void Draw()
{
  cout << "三目並べ" << endl;
  for (int i = 0; i < 3; i++){
    for (int j = 0; j < 3; j++) {
      cout << matrix[i][j] << " ";
    }
    cout << endl;
  }
}

void Input() {
  int a;
  cout << "1~9の空いている数字を選んでください";
  cin >> a;

  if (a == 1)
    matrix[0][0] = player;
  else if (a == 2)
    matrix[0][1] = player;
  else if (a == 3)
    matrix[0][2] = player;
  else if (a == 4)
    matrix[1][0] = player;
  else if (a == 5)
    matrix[1][1] = player;
  else if (a == 6)
    matrix[1][2] = player;
  else if (a == 7)
    matrix[2][0] = player;
  else if (a == 8)
    matrix[2][1] = player;
  else if (a == 9)
    matrix[2][2] = player;
}
void TogglePlayer() {
  if (player == 'X')
    player = 'O';
  else
    player = 'X';
}

char Win()
{
  //X プレイヤー
  //横
  if (matrix[0][0] == 'X' && matrix[0][1] == 'X' && matrix[0][2] == 'X')
    return 'X';
  if (matrix[1][0] == 'X' && matrix[1][1] == 'X' && matrix[1][2] == 'X')
    return 'X';
  if (matrix[2][0] == 'X' && matrix[2][1] == 'X' && matrix[2][2] == 'X')
    return 'X';
//縦  
  if (matrix[0][0] == 'X' && matrix[1][0] == 'X' && matrix[2][0] == 'X')
    return 'X';
  if (matrix[0][1] == 'X' && matrix[1][1] == 'X' && matrix[2][1] == 'X')
    return 'X';
  if (matrix[0][2] == 'X' && matrix[1][2] == 'X' && matrix[2][2] == 'X')
    return 'X';
  //斜め
  if (matrix[0][0] == 'X' && matrix[1][1] == 'X' && matrix[2][2] == 'X')
    return 'X';
  if (matrix[2][0] == 'X' && matrix[1][1] == 'X' && matrix[0][2] == 'X')
    return 'X';

  //O　プレイヤー
    //横
  if (matrix[0][0] == 'O' && matrix[0][1] == 'O' && matrix[0][2] == 'O')
    return 'O';
  if (matrix[1][0] == 'O' && matrix[1][1] == 'O' && matrix[1][2] == 'O')
    return 'O';
  if (matrix[2][0] == 'O' && matrix[2][1] == 'O' && matrix[2][2] == 'O')
    return 'O';
//縦  
  if (matrix[0][0] == 'O' && matrix[1][0] == 'O' && matrix[2][0] == 'O')
    return 'O';
  if (matrix[0][1] == 'O' && matrix[1][1] == 'O' && matrix[2][1] == 'O')
    return 'O';
  if (matrix[0][2] == 'O' && matrix[1][2] == 'O' && matrix[2][2] == 'O')
    return 'O';
  //斜め
  if (matrix[0][0] == 'O' && matrix[1][1] == 'O' && matrix[2][2] == 'O')
    return 'O';
  if (matrix[2][0] == 'O' && matrix[1][1] == 'O' && matrix[0][2] == 'O')
    return 'O';

  return '/';
}

int main() {
  Draw();
  while (1) {
    Input();
    Draw();
    if(Win() == 'X')
    {
      cout << "Xの勝ち！" << endl;
      break;
    }
    else if(Win() == 'O')
    {
      cout << "Oの勝ち！" << endl;
      break;
    }
    TogglePlayer();
  }
  system("pause");
  return 0;
}