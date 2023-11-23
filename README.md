- 👋 Hi, I’m @saikeerthi509
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
saikeerthi509/saikeerthi509 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
def analyzeboard(board):
  cb=[[0,1,2],[3,4,5],[6,7,8],[0,3,6],[1,4,7],[2,5,8],[0,4,8],[2,4,6]]
  for i in range(0,8):
    if(board[cb[i][0]]!=0 and board[cb[i][0]]==board[cb[i][1]] and board[cb[i][1]]==board[cb[i][2]] ):
      return board[cb[i][0]]
    else:
      return 0

  x=analyzeboard(board)
  if(x==0):
    constboard(board)
    print("draw")
  if(x==-1):
    constboard(board)
    print("player 0 has won")
  if(x==1):
    constboard(board)
    print("player x has won")
def constboard(board):
  print("current state of board is:\n")
  for i in range(0,9):
    if((i>0)and (i%3==0)):
      print("\n")
    if(board[i]==0):
      print("_",end=" ")
    if(board[i]==1):
      print("x",end=" ")
    print("\n\n")
def user1turn(board):
  pos=input("enter x position")
  pos=int(pos)
  if(board[pos-1]!=0):
    print("wrong move")
    exit(0)
  board[pos-1]=1
def user2turn(board):
  pos=input("enter 0 position")
  pos=int(pos)
  if(board[pos-1]!=0):
    print("wrong move")
    exit(0)
  board[pos-1]=-1
def compturn(board):
  pos=-1;
  value=-2
  for i in range(0,9):
    if(board[i]==0):
      board[i]=1;
      score=-minmax(board,-1)
      board[i]=0;
      if(score>value):
        value=score
        pos=i
  board[pos]=1
def minmax(board,player):
  x=analyzeboard(board);
  if(x!=0):
    return (x*player);
  pos=-1;
  value=-2
  for i in range(0,9):
    if(board[i]==0):
      board[i]=player;
      score=-minmax(board,player*-1)
      board[i]=0;
      if(score>value):
        value=score
        pos=i
  if(pos==-1):
    return 0;




























def main():
  choice=int(input("enter 1 for single player and 2 for multiplayer"))
  board=[0,0,0,0,0,0,0,0]
  if(choice==1):
    print("computer:0 vs you:x")
    player=int(input("enter if u want to play 1(st) or 2(nd)"))
    for i in range(0,9):
      if(analyzeboard(board)!=0):
        break;
      if((i+player)%2==0):
        compturn(board);
      else:
        constboard(board);
        user1turn(board);





