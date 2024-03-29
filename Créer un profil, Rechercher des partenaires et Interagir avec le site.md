import tkinter as tk
from tkinter import ttk
from tkinter import messagebox

window = tk.Tk()
window.title("Trouver un partenaire")
window.geometry("800x600")

notebook = ttk.Notebook(window)

tab_creer_profil = ttk.Frame(notebook)
tab_rechercher = ttk.Frame(notebook)
tab_interactions = ttk.Frame(notebook)

notebook.add(tab_creer_profil, text="Créer un profil")
notebook.add(tab_rechercher, text="Rechercher des partenaires")
notebook.add(tab_interactions, text="Interagir avec le site")

notebook.pack(expand=1, fill="both")

# Créer un profil
tk.Label(tab_creer_profil, text="Nom d'utilisateur : ").grid(row=0, column=0)
tk.Label(tab_creer_profil, text="Mot de passe : ").grid(row=1, column=0)
tk.Label(tab_creer_profil, text="Confirmer le mot de passe : ").grid(row=2, column=0)
tk.Label(tab_creer_profil, text="Âge : ").grid(row=3, column=0)
tk.Label(tab_creer_profil, text="Sexe : ").grid(row=4, column=0)

username_entry = tk.Entry(tab_creer_profil)
password_entry = tk.Entry(tab_creer_profil, show="*")
confirm_password_entry = tk.Entry(tab_creer_profil, show="*")
age_spinbox = tk.Spinbox(tab_creer_profil, from_=18, to=100)
gender_combobox = ttk.Combobox(tab_creer_profil, values=["Homme", "Femme", "Autre"])

username_entry.grid(row=0, column=1)
password_entry.grid(row=1, column=1)
confirm_password_entry.grid(row=2, column=1)
age_spinbox.grid(row=3, column=1)
gender_combobox.grid(row=4, column=1)

def create_profile():
    messagebox.showinfo("Profil créé", "Votre profil a été créé avec succès !")

create_button = ttk.Button(tab_creer_profil, text="Créer un profil", command=create_profile)
create_button.grid(row=5, column=1, pady=(10, 0))

# Rechercher des partenaires
tk.Label(tab_rechercher, text="Âge minimum : ").grid(row=0, column=0)
tk.Label(tab_rechercher, text="Âge maximum : ").grid(row=1, column=0)
tk.Label(tab_rechercher, text="Sexe : ").grid(row=2, column=0)

min_age_spinbox = tk.Spinbox(tab_rechercher, from_=18, to=100)
max_age_spinbox = tk.Spinbox(tab_rechercher, from_=18, to=100)
search_gender_combobox = ttk.Combobox(tab_rechercher, values=["Homme", "Femme", "Autre"])

min_age_spinbox.grid(row=0, column=1)
max_age_spinbox.grid(row=1, column=1)
search_gender_combobox.grid(row=2, column=1)

def search_partners():
    messagebox.showinfo("Recherche", "La recherche de partenaires a été lancée !")

search_button = ttk.Button(tab_rechercher, text="Rechercher des partenaires", command=search_partners)
search_button.grid(row=3, column=1, pady=(10, 0))

# Interagir avec le site
def send_message():
    messagebox.showinfo("Message envoyé", "Votre message a été envoyé avec succès !")

tk.Label(tab_interactions, text="Destinataire : ").grid(row=0, column=0)
tk.Label(tab_interactions, text="Message : ").grid(row=1, column=0)

recipient_entry = tk.Entry(tab_interactions)
message_text = tk.Text(tab_interactions, height=10, width=50)

recipient_entry.grid(row=0, column=1)
message_text.grid(row=1, column=1)

send_button = ttk.Button(tab_interactions, text="Envoyer le message", command=send_message)
send_button.grid(row=2, column=1, pady=(10, 0))

window.mainloop()
