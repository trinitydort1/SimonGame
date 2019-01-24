# SimonGame
Memory Game 
import tkinter as tk

class Simon:
  def __init__(self,parent):
    self.parent = parent
    self.canvas = tk.Canvas(parent)
    self.draw_board()
# draw simon board: four squares: red, green, blue, and yellow
  def draw_board(self):
    self.canvas.destroy()
    self.canvas = tk.Canvas(self.parent, height=400, width=400)
    self.canvas.pack()
# dark is the color of board before it lights to show pattern to be copied
    self.dark {'r':'darkred', 'g':'darkgreen','b':'darkblue','y':'darkgoldenrod'}
# light is color of board when pattern is being displayed 
    self.light {'r':'red', 'g':'green','b':'blue', 'y':'yellow'}
# set colors for board
    self.squres = { 'r':self.canvas.create_rectangle(0, 0, 200, 200, 
    fill = 'darkred', outline = 'darkred' )
                    'g':self.canvas.create_rectangle(200, 0, 400, 200, 
    fill = 'darkgreen', outline = 'darkgreen' )
                    'b':self.canvas.create_rectangle(0, 200, 200, 400, 
    fill = 'darkblue', outline = 'darkblue' )
                    'y':self.canvas.create_rectangle(200, 200, 400, 400, 
    fill = 'darkgoldenrod', outline = 'darkgoldenrod')}
# dict.
self.ids = {v:k for k,v in self.squares.items()}
self.score = 0
# board shows pattern 
# note: lambda is small function 
    self.status = tk.Label(root, text= "Play if you are feeling brave")
    self.status.pack()
    self.parent.bind('<h>', self.score)
    self.draw_board()
  def draw_board(self):
    self.pattern = 'rgbyr' #random.choice('rgby')
    self.selections = []
    self.parent.after(1000, self.animate)
  def animate(self, idx = 0):
      c = self.pattern[idx]
      self.canvas.intemconfig(self.squares[c](fill=self.light[c], outline=self.light[c])
      self.parent.after(1000, lambda: self.canvas.itemconfig(fill=self.dark[c], outline=self.dark[c]))
# user to select square
      inx += 1
      if idx < len(self.pattern):
        self.parent.after(1000, lambda: self.animate(idx))
      else:
        self.canvas.bind('<1>', self.select)
        print(self.pattern)
        # for key, square in self.squares.items():
          # square.bind('<1>', lambda key=key: self.select(key))
  def select(self,event= None):
    id = self.canvas.find_withtag("CURRENT")[0]
    color = self.ids[id]
    self.selections += color
    #id = tk.CURRENT
    #self.selections += self.ids[tk.CURRENT]
    self.canvas.itemconfig(id ,fill=self.light[color], outline=self.light[color]))
    self.parent.after(1000, lambda.self.canvas.itemconfig(id,fill=self.dark[color], outline=self.dark[color]))
    #for key,square in self.squares.items():
    #square.bind('<1>')
# if user guessed pattern is correct 
    if self.pattern == self.selections:
      self.pattern += random.choice
      self.selections = ''
      self.score = len(self.pattern)
      self.animate()
# reset the game if user guesses wrong pattern 
    elif self.pattern[len(self.selections)-1]!= color:
      self.canvas.unbind()
      self.status.config(text = "Not Today!")
      self.parent,after(1000 lambda: self.status.config(text =''))
      self.parent.after(1000, self.draw_board)
      print(self.pattern, self.selections)
# when user gets it right it should say something nice :)
  def score(self, event=None):
    self.status.config(text = self.score)
    self.parent.after(2000, lambda:self.status.config("You're doing great sweetie!")
      #self.draw_board()
root = tk.Tk
Simon = Simon(root)
root.mainloop()
