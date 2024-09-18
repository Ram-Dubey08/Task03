# Task03: Creating GUI to Extract Lyrics from song Using python
from tkinter import *
from lyricsgenius import Genius

def extract_lyrics():
    song = song_entry.get()
    artist = artist_entry.get()
    genius = Genius("PvctUGPS-gffkNl8Tbo8a8_Sk-LIf2ZATnjQm0ZZpI7szPtmkXlZcLEn8F0RYJ4l")  # Replace with your Genius API access token
    song = genius.search_song(song, artist)
    
    if song is not None:
        lyrics_text.delete(1.0, END)
        lyrics_text.insert(END, song.lyrics)
    else:
        lyrics_text.delete(1.0, END)
        lyrics_text.insert(END, "Lyrics not found.")


window = Tk()
window.title("Lyrics Extractor")
window.geometry("400x300")


song_label = Label(window, text="Song Name:")
song_label.pack()

song_entry = Entry(window)
song_entry.pack()

artist_label = Label(window, text="Artist:")
artist_label.pack()

artist_entry = Entry(window)
artist_entry.pack()


extract_button = Button(window, text="Extract Lyrics", command=extract_lyrics)
extract_button.pack()
lyrics_text = Text(window, wrap=WORD, height=10)
lyrics_text.pack()
window.mainloop()
