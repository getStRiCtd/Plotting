import sys
import tkinter as tk
import matplotlib
import matplotlib.pyplot as plt
from matplotlib.backends.backend_tkagg import FigureCanvasTkAgg as FigureCanvas

matplotlib.use('TkAgg')

class Frames:
    def __init__(self):
        self.frame_1 = tk.Frame(self)
        self.frame_1.grid()

        self.frame_2 = tk.Frame(self)
        self.frame_2.grid(row=1)

        self.frame_3 = tk.Frame(self)
        self.frame_3.grid(row=2)
        

class MainWindow(tk.Frame):
    '''
    Главное окно
    Функции - создать окно с графом, создать окно с текстом
    '''

    counter_simple = counter_graph = 0

    def __init__(self):
        tk.Frame.__init__(self)
        self.button = tk.Button(self, text='Create new window', 
                                command=self.create_window)
        self.button.grid(row=1, column=1)

        self.button_1 = tk.Button(self, text='Create Graph window',
                                    command=self.create_graph_window)
        self.button_1.grid(row=1, column=2, sticky=tk.E)

    
    def create_window(self):
        self.counter_simple += 1
        t = tk.Toplevel(self)
        t.title('Window #%s' % self.counter_simple)
        l = tk.Label(t, text='This is window #%s' % self.counter_simple)
        l.pack(side='top', fill='both', pady=100, padx=100, expand=True)
    
    def create_graph_window(self):
        self.counter_graph += 1
        window = GraphWindow()

        window.columnconfigure(0, weight=1)
        window.rowconfigure(1, weight=1)

        window.title('Graph window #%s' % self.counter_graph)


class GraphWindow(tk.Toplevel, Frames):
    def __init__(self):
        tk.Toplevel.__init__(self)
        Frames.__init__(self)
        
        self.x_coord = tk.IntVar()
        self.y_coord = tk.IntVar()
        self.frame_2.input = tk.Entry(master=self.frame_2, textvariable=self.x_coord)
        self.frame_2.input.grid(row=0, column=1)

        self.frame_2.input_x = tk.Entry(master=self.frame_2, textvariable=self.x_coord)
        self.frame_2.input_x.grid(row=0, column=0)

        self.frame_2.input_y = tk.Entry(master=self.frame_2, textvariable=self.y_coord)
        self.frame_2.input_y.grid(row=0, column=1)

        self.frame_3.action = tk.Button(master=self.frame_3, text='Wow that\'s work',
                                        command=self.draw_graph)
        self.frame_3.action.grid()

        self.f = plt.figure(figsize=(10, 5))

        self.canvas = FigureCanvas(self.f, self.frame_1)
        
        self.canvas.get_tk_widget().grid()

    def plotting_graph(self):
        self.f.clear()
        x, y = self.x_coord.get(), self.y_coord.get()
        self.ax0 = self.f.add_subplot()
        return self.ax0.scatter(x, y)

    def draw_graph(self):
        self.plotting_graph()
        self.canvas.draw()


if __name__ == '__main__':
    root = tk.Tk()

    main = MainWindow()
    main.grid()

    root.mainloop()
