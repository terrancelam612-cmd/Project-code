import tkinter as tk


class FirstWindow(tk.Frame):
    def __init__(self, parent):
        super().__init__(parent, background="red")
        tk.Label(self, text="MC", bg="red", font=('Arial', 18)).pack(padx=10, pady=10)

        self.blocks = ["A", "B"]
        self.blockIndex = 0
        self.blockLabel = tk.Label(self, text="Block: " + self.blocks[self.blockIndex],
                                   bg="red", font=('Arial', 18))
        self.blockLabel.pack(padx=10, pady=10)

        self.floors = ["G/F", "1/F", "2/F", "3/F"]
        self.floorIndex = 0
        self.floorLabel = tk.Label(self, text="Floor: " + self.floors[self.floorIndex],
                                   bg="red", font=('Arial', 18))
        self.floorLabel.pack(padx=10, pady=10)
        self.pack(expand=True, fill=tk.BOTH)

    def changeBlock(self):
        self.blockIndex = (self.blockIndex + 1) % len(self.blocks)
        self.blockLabel.config(text="Block: " + self.blocks[self.blockIndex])

    def changeFloor(self):
        self.floorIndex = (self.floorIndex + 1) % len(self.floors)
        self.floorLabel.config(text="Floor: " + self.floors[self.floorIndex])


class SecondWindow(tk.Frame):
    def __init__(self, parent):
        super().__init__(parent, background="green")
        tk.Label(self, text="This is JCC", bg="green", font=('Arial', 18)).pack(padx=10, pady=10)

        self.blocks = ["C", "D"]
        self.blockIndex = 0
        self.blockLabel = tk.Label(self, text="Block: " + self.blocks[self.blockIndex],
                                   bg="green", font=('Arial', 18))
        self.blockLabel.pack(padx=10, pady=10)

        self.floors = ["G/F", "1/F", "2/F", "3/F", "4/F", "5/F"]
        self.floorIndex = 0
        self.floorLabel = tk.Label(self, text="Floor: " + self.floors[self.floorIndex],
                                   bg="green", font=('Arial', 18))
        self.floorLabel.pack(padx=10, pady=10)
        self.pack(expand=True, fill=tk.BOTH)

    def changeBlock(self):
        self.blockIndex = (self.blockIndex + 1) % len(self.blocks)
        self.blockLabel.config(text="Block: " + self.blocks[self.blockIndex])

    def changeFloor(self):
        self.floorIndex = (self.floorIndex + 1) % len(self.floors)
        self.floorLabel.config(text="Floor: " + self.floors[self.floorIndex])


class ThirdWindow(tk.Frame):
    def __init__(self, parent):
        super().__init__(parent, background="blue")
        tk.Label(self, text="This is IOH", bg="blue", font=('Arial', 18)).pack(padx=10, pady=10)

        self.blocks = ["Main Block"]
        self.blockIndex = 0
        self.blockLabel = tk.Label(self, text="Block: " + self.blocks[self.blockIndex],
                                   bg="blue", font=('Arial', 18))
        self.blockLabel.pack(padx=10, pady=10)

        self.floors = ["B1", "G/F", "1/F", "2/F"]
        self.floorIndex = 0
        self.floorLabel = tk.Label(self, text="Floor: " + self.floors[self.floorIndex],
                                   bg="blue", font=('Arial', 18))
        self.floorLabel.pack(padx=10, pady=10)
        self.pack(expand=True, fill=tk.BOTH)

    def changeBlock(self):
        self.blockIndex = (self.blockIndex + 1) % len(self.blocks)
        self.blockLabel.config(text="Block: " + self.blocks[self.blockIndex])

    def changeFloor(self):
        self.floorIndex = (self.floorIndex + 1) % len(self.floors)
        self.floorLabel.config(text="Floor: " + self.floors[self.floorIndex])


class MainWindow:
    def __init__(self, master):
        mainframe = tk.Frame(master)
        mainframe.pack(expand=True, fill=tk.BOTH)
        self.index = 0

        self.frameList = [FirstWindow(mainframe),
                          SecondWindow(mainframe),
                          ThirdWindow(mainframe)]
        self.frameList[1].pack_forget()
        self.frameList[2].pack_forget()

        bottomframe = tk.Frame(master)
        bottomframe.pack(padx=10, pady=10)

        switch = tk.Button(bottomframe, text="Switch", command=self.changeWindows)
        switch.pack(padx=10, pady=10)

        block = tk.Button(bottomframe, text="Block", command=self.changeBlock)
        block.pack(padx=10, pady=10)

        floor = tk.Button(bottomframe, text="Floor", command=self.changeFloor)
        floor.pack(padx=10, pady=10)

    def changeWindows(self):
        self.frameList[self.index].pack_forget()
        self.index = (self.index + 1) % len(self.frameList)
        self.frameList[self.index].pack(expand=True, fill=tk.BOTH, padx=10, pady=10)

    def changeBlock(self):
        self.frameList[self.index].changeBlock()

    def changeFloor(self):
        self.frameList[self.index].changeFloor()


root = tk.Tk()
window = MainWindow(root)
root.mainloop()
