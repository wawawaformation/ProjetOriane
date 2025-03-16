# Projet Citations – Vue d’Ensemble

Le projet **Citations** est une plateforme permettant à tout utilisateur d'accéder à une base de **citations célèbres** et à leurs explications, associées à des auteurs référencés. L’objectif est de fournir un espace où chacun peut **consulter, partager et enrichir** un répertoire de citations inspirantes, éducatives ou humoristiques.

L’application propose **une API publique** permettant d’accéder aux citations et aux auteurs. Les utilisateurs avec des rôles spécifiques peuvent **ajouter, modifier ou supprimer** des contenus, tandis que les administrateurs gèrent l’accès et les comptes utilisateurs.

---

## Règles de gestion du fil rouge

### 1. Accès aux données
- **Tout le monde** peut **voir** les citations, les auteurs et utiliser l’API publique.

### 2. Gestion des auteurs
- Un auteur est identifié par :
  - **Son nom d’auteur** (unique dans la base).
  - **Sa date de naissance**.
  - **Sa date de décès** (si applicable).
  - **Une biographie**.
  - **Une photo** (optionnelle).

### 3. Gestion des citations
- Une citation est composée de :
  - **Le texte de la citation**.
  - **Une explication** de la citation.
- Une citation est **écrite par un et un seul auteur** ou peut être **anonyme**.

### 4. Gestion des rôles
- Une personne peut posséder **un ou plusieurs rôles**.
- **Rôles disponibles** :
  - **Administrateur** :
    - Peut **gérer** (CRUD) les utilisateurs.
  - **Éditeur** :
    - Peut **gérer** (CRUD) les citations et les auteurs.

### 5. CRUD (Create, Read, Update, Delete)
Le terme **CRUD** désigne les **quatre opérations fondamentales** sur les données :
- **C**reate (**Créer**) → Ajouter une nouvelle donnée.
- **R**ead (**Lire**) → Consulter les données existantes.
- **U**pdate (**Mettre à jour**) → Modifier une donnée existante.
- **D**elete (**Supprimer**) → Effacer une donnée.

### 6. Gestion des utilisateurs
- Un utilisateur est défini par :
  - **Nom**.
  - **Prénom**.
  - **Email**.
  - **Mot de passe** (chiffré en base de données).

### 7. Procédure de récupération de mot de passe oublié
1. L’utilisateur effectue une demande de réinitialisation de mot de passe.
2. Un **jeton unique** est généré et stocké temporairement dans son compte utilisateur.
3. Un email est envoyé contenant un **lien de réinitialisation** avec ce jeton.
4. L’utilisateur clique sur le lien, saisit un **nouveau mot de passe**.
5. Une fois confirmé, le **mot de passe est mis à jour** et le jeton supprimé.
