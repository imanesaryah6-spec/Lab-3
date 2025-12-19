# Lab-3
Python 
def calcul_reduction(prix, est_etudiant, annees_fidelite):
    """
    Calcule le prix final après application des remises :
    - 10% si étudiant
    - 15% si fidélité >= 5 ans
    - 5€ fixe si prix > 100€
    """
    remise_totale = 0.0

    # 1. Remise étudiant (10%)
    if est_etudiant == "o":
        remise_totale += prix * 0.10
    
    # 2. Remise fidélité (15% si 5 ans ou plus)
    if annees_fidelite >= 5:
        remise_totale += prix * 0.15
        
    # 3. Remise supplémentaire (5€ si prix initial > 100€)
    if prix > 100:
        remise_totale += 5.0
        
    # Calcul du prix final et vérification (ne doit pas être négatif)
    prix_final = prix - remise_totale
    if prix_final < 0:
        prix_final = 0
        
    return prix_final, remise_totale

# --- Programme Principal ---
print("--- Système de Calcul de Réduction ---")

while True:
    try:
        # Saisie du prix initial
        p_initial = float(input("\nPrix du produit (€) [ou 0 pour quitter] : "))
        if p_initial == 0:
            break
            
        # Saisie des informations client
        statut = input("Êtes-vous étudiant ? (o/n) : ").strip().lower()
        fidelite = int(input("Années de fidélité : "))
        
        # Appel de la fonction de calcul
        final, remise = calcul_reduction(p_initial, statut, fidelite)
        
        # Affichage des résultats
        print(f"-> Prix initial : {p_initial}€")
        print(f"-> Total des remises : {remise}€")
        print(f"-> Prix final à payer : {final}€")
        
    except ValueError:
        # Gestion des erreurs de saisie
        print("Erreur : Veuillez saisir des valeurs numériques valides.")

print("Merci d'avoir utilisé le programme !")
