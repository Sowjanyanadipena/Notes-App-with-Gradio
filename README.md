# 📝 Simple Notes App (Gradio)
A minimal **full-stack-like Notes Application** built with **Python** and **Gradio UI**.  
This app lets you **add, view, and delete notes** with a clean interface and **runs seamlessly in Google Colab** without any extra setup.
## ✅ Features
- Add new notes (Title + Content)
- View all notes dynamically
- Delete notes by index
- Clean UI powered by **Gradio**
- **No ngrok, no token, no signup required**
- Runs in **Colab or local machine**
## 🛠 Tech Stack
- **Frontend**: [Gradio](https://gradio.app/)
- **Backend**: Python Functions
- **Database**: In-memory (no external DB needed)
## 🚀 How to Run in Google Colab
1. Open [Google Colab](https://colab.research.google.com/).
2. Copy and paste the code below:
```python
!pip install gradio
import gradio as gr
# In-memory storage for notes
notes = []
# Functions for CRUD
def add_note(title, content):
    if title.strip() and content.strip():
        notes.append({"title": title, "content": content})
    return display_notes()
def delete_note(index):
    if 0 <= index < len(notes):
        notes.pop(index)
    return display_notes()
def display_notes():
    if not notes:
        return "No notes yet."
    result = ""
    for i, note in enumerate(notes):
        result += f"{i}. **{note['title']}**: {note['content']}\n"
    return result
# Gradio UI
with gr.Blocks() as demo:
    gr.Markdown("# 📝 Simple Notes App") 
    with gr.Row():
        title = gr.Textbox(label="Title")
        content = gr.Textbox(label="Content")
    with gr.Row():
        add_btn = gr.Button("Add Note")
    notes_display = gr.Markdown("No notes yet.")
    index_to_delete = gr.Number(label="Note Index to Delete (0-based)", precision=0)
    delete_btn = gr.Button("Delete Note")

    add_btn.click(add_note, [title, content], notes_display)
    delete_btn.click(delete_note, index_to_delete, notes_display)
demo.launch(share=True)
3. Click **Run**, and you will get a **public shareable link**.
## 📂 Folder Structure (if using locally)
notes-app/
│
├── app.py          # Main app script
├── README.md       # Documentation
└── requirements.txt # Dependencies
## ✅ Install & Run Locally
```bash
git clone https://github.com/yourusername/notes-app.git
cd notes-app
pip install -r requirements.txt
python app.py
## 📦 requirements.txt
gradio
## 🎯 Why This Project?
This is a beginner-friendly **full-stack style project** for practicing:
- UI design with Gradio
- Handling state in Python
- Simple CRUD logic
## 📜 License
MIT License
