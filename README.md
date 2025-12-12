# 🎵 Local Music Player & Playlist Manager (C Project)

A fully local music player and playlist manager written in **C**, using multiple data structures like **Binary Search Tree**, **Adjacency List**, **Doubly Linked List**, and **Two Stacks** to manage songs, playback history, and playlist navigation.

Playback is powered by **`ffplay` (FFmpeg)**, and the project supports **Windows and Linux** with OS-specific handling for threads and process execution.


## 🎥 Demo Video

Watch the full demo of the Local Music Player & Playlist Manager:

👉 **[Click to watch the demo](https://github.com/Krishiv1808/DSA-MINIPROJECT/releases/download/v1.0/Demo.mp4)**

---

## 🚀 Features

- 📥 Add or download songs into the **`localdatabase`** folder  
- 📂 Create custom **playlists (folders)**  
- 📁 Copy songs from `localdatabase` → playlist folders  
- ▶️ Load a playlist and play songs sequentially  
- ⏭️ Navigate **next / previous** tracks  
- 🔁 Background looping playlist playback using threads  
- 🔍 Search songs by **prefix** or **artist name** using a case-insensitive **BST**  
- 📜 View all playlists and the songs inside them  
- 🧱 Two-stack playback history system:
  - **Stack 1** → backward history  
  - **Stack 2** → forward navigation  
- 💻 Works on **Windows & Linux**

---

## 🧩 Data Structures Used

### 1️⃣ Binary Search Tree (BST)
**Stores:**
- filename  
- full path  

**Used for:**
- Fast prefix/artist search  
- Case-insensitive comparisons  
- Returning multiple matched results  

---

### 2️⃣ Adjacency List (Playlist Manager)
Each playlist folder is treated as a **node**, containing a linked list of songs.

**Used for:**
- Viewing playlists and their contents  
- Managing songs inside playlist folders  

---

### 3️⃣ Doubly Linked List (Runtime Playlist Loader)

Used when a playlist is loaded into memory: prev ← [SongNode] → next


**Supports:**
- Next (`L`)  
- Previous (`J`)  
- Continuous looping playback  

---

### 4️⃣ Two Stacks (Playback History)

✔ **Stack 1 (`head`) – Primary Backward History**  
✔ **Stack 2 (`head1`) – Forward History**

Used for:
- Backward navigation  
- Forward navigation  
- Avoiding repeat conflicts during navigation  
- Maintaining history while playing manually or via threads  

---

## 🛠 Requirements

- C compiler — GCC / Clang / MSVC / MinGW  
- FFmpeg installed (must have **`ffplay`** in PATH)  
- POSIX Threads (Linux/macOS)  
- Windows API (for process/thread handling)

---

## 🔧 Build Instructions

### Linux / macOS
```
gcc musicplayer.c -o musicplayer
```
### Windows(MinGW)
```gcc musicplayer.c -o musicplayer```

## ▶️ Running the Program

1. Create a folder named **localdatabase**  
2. Add **MP3 songs** into it  
3. Run the program:  
   ```bash
   ./musicplayer
4. The BST (Binary Search Tree) automatically builds from the localdatabase on startup.

## 🎮 Menu Commands

| Key       | Action                                                  |
| --------- | ------------------------------------------------------- |
| **V**     | View all playlists and their songs                      |
| **C**     | Create new playlist folder                              |
| **P**     | Load and play songs from a chosen directory             |
| **F**     | Search & play song using BST prefix search              |
| **E / A** | Search and copy song from localdatabase into a playlist |
| **L**     | Play next song                                          |
| **J**     | Play previous song                                      |
| **K**     | Stop currently playing song                             |
| **T**     | Show current playlist (doubly linked list)              |
| **1**     | Change directory to parent (`cd ..`)                    |
| **2**     | Change directory to `DSA-MINIPROJECT`                   |
| **0**     | Exit program                                            |

---

## ⚙️ Important Behaviors

### 🔁 Background Playback Thread
- Runs in parallel and loops through the playlist until stopped.  
- Stopping or skipping songs automatically terminates any active playback thread.

### 🔍 BST Prefix Search
- Case-insensitive.  
- Returns all matching songs starting with the entered prefix.

### 📁 Copying Songs
- Copies files from **localdatabase → selected playlist folder**.  
- Ensures playlists behave like independent music directories.

### 🔄 Two-Stack Navigation System
- One stack tracks **forward navigation**.  
- One stack tracks **backward navigation**.  
- Prevents conflicts between manual navigation and background playback logic.
