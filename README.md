import tkinter as tk

class FirstWindow(tk.Frame):
    def _init_(self, parent):
        super()._init_(parent, background="red")
        tk.Label(self, text=" MC").pack(padx=10, pady=10)

class SecondWindow(tk.Frame):
    def _init_(self, parent):
        super()._init_(parent, background="green")
        tk.Label(self, text="This is JCC").pack(padx=10, pady=10)

class MainWindow:
    def _init_(self, master):
        master.geometry("320x160")
        self.mainframe = tk.Frame(master)
        self.mainframe.pack(padx=10, pady=10, fill="both", expand=True)
        self.index = 0

        self.frameList = [FirstWindow(self.mainframe), SecondWindow(self.mainframe)
        self.frameList.pack(expand=True, fill=tk.BOTH)]

        bottomframe = tk.Frame(master)
        bottomframe.pack(padx=10, pady=10)
        tk.Button(bottomframe, text="Switch", command=self.switchWindows).pack(padx=10, pady=10)

    def switchWindows(self):
        self.frameList[self.index].pack_forget() 
        self.index = (self.index + 1) % len(self.frameList)
        self.frameList[self.index].pack(expand=True, fill=tk.BOTH)

root = tk.Tk()
window = MainWindow(root)
root.mainloop()
