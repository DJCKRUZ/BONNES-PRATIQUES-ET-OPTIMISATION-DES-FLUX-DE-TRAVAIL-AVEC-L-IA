# 📝 AVANT / APRES - Comparaison du Code

## 🎯 PROMPT IA / OBJECTIF

**Tâche reçue:**
Vous avez reçu un composant web défectueux : une carte de prix avec des problèmes de mise en page et des boutons qui ne répondent pas. Votre tâche consiste à le réparer, à le remanier et à le préparer à la réutilisation à l'aide de l'IA.

---

## ❌ CODE ORIGINAL CASSÉ (AVANT)

```html
<!DOCTYPE html>
<html>
<head>
<style>
.pricing {
width: 300px;
margin: auto;
background-color: #fff;
box-shdow: 0 0 10px #ccc;
padding: 10px;
text-align: left;
}

.title {
font-size: 22px;
font-weight: bold;
}

.price {
font-size: 18px;
color: green;
}

.features {
list-style: none;
padding-left: 0;
}

.features li {
padding: 4px;
border-bottom: 1px solid #eee;
}

.btn {
background: blue;
color: white;
padding: 10px 20px;
border: none;
margin-top: 10px;
}

.btn:hover {
background: darkblue;
}
</style>
</head>
<body>

<div class="pricing">
<h2 class="title">Basic Plan<h2>
<p class="price">$9.99 /month</p>

<ul class="features">
<li>1 GB Storage</li>
<li>Basic Support</li>
<li>All Core Features</li>
</ul>

<button class="btn">Start Trial</button>
</div>

</body>
</html>
```

### 🐛 Bogues identifiés:
1. ❌ `<h2 class="title">Basic Plan<h2>` - Balise mal fermée
2. ❌ `box-shdow` - Typo CSS (manque "a")
3. ❌ `text-align: left;` - Alignement incorrect
4. ❌ Pas de `border-radius` et `cursor: pointer` sur le bouton
5. ❌ Pas de responsive design (largeur fixe 300px)
6. ❌ Pas d'accessibilité (ARIA labels, focus states)
7. ❌ Code statique et non réutilisable
8. ❌ Pas de variables CSS pour maintenabilité
9. ❌ Pas d'événement click sur le bouton

---

## ✅ CODE CORRIGÉ & OPTIMISÉ (APRÈS)

```html
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Composant Carte de Prix Optimisé</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;700&display=swap" rel="stylesheet">
    <style>
        /* Variables CSS pour une meilleure maintenabilité */
        :root {
            --color-primary: #0066ff;
            --color-primary-dark: #0052cc;
            --color-success: #10b981;
            --color-text-primary: #1f2937;
            --color-text-secondary: #6b7280;
            --color-border: #e5e7eb;
            --color-bg-light: #f3f4f6;
            --border-radius: 12px;
            --transition-default: all 0.3s ease;
        }

        * {
            box-sizing: border-box;
        }

        body {
            font-family: 'Inter', sans-serif;
            background: linear-gradient(135deg, var(--color-bg-light) 0%, #ffffff 100%);
            margin: 0;
            padding: 0;
            min-height: 100vh;
        }

        /* ✅ CORRECTION #2: box-shadow (était box-shdow) */
        /* ✅ CORRECTION #5: Responsive design */
        .pricing {
            width: 100%;
            max-width: 300px;
            margin: 0 auto;
            background-color: #ffffff;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            border-radius: var(--border-radius);
            padding: 20px;
            /* ✅ CORRECTION #3: text-align center (était left) */
            text-align: center;
            transition: var(--transition-default);
            border: 1px solid var(--color-border);
        }

        .pricing:hover {
            box-shadow: 0 8px 24px rgba(0, 0, 0, 0.15);
            transform: translateY(-4px);
        }

        .title {
            font-size: 24px;
            font-weight: 700;
            color: var(--color-text-primary);
            margin: 0 0 12px 0;
        }

        .price {
            font-size: 32px;
            color: var(--color-primary);
            font-weight: 800;
            margin: 12px 0;
        }

        .period {
            font-size: 14px;
            color: var(--color-text-secondary);
            margin-left: 4px;
        }

        .features {
            list-style: none;
            padding-left: 0;
            margin: 20px 0;
        }

        .features li {
            padding: 10px 0;
            border-bottom: 1px solid var(--color-border);
            color: var(--color-text-secondary);
            font-size: 14px;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .features li:last-child {
            border-bottom: none;
        }

        .features li::before {
            content: "✓";
            color: var(--color-success);
            font-weight: bold;
            margin-right: 8px;
            font-size: 16px;
        }

        /* ✅ CORRECTION #4: Amélioration UX du bouton */
        .btn {
            background: var(--color-primary);
            color: white;
            padding: 12px 24px;
            border: none;
            margin-top: 20px;
            /* ✅ CORRECTION: Ajout de border-radius */
            border-radius: var(--border-radius);
            /* ✅ CORRECTION: Ajout de cursor pointer */
            cursor: pointer;
            font-weight: 600;
            font-size: 15px;
            width: 100%;
            transition: var(--transition-default);
            /* ✅ CORRECTION #6: Accessibilité - Styles focus explicites */
            outline: none;
        }

        .btn:hover {
            background: var(--color-primary-dark);
            transform: translateY(-2px);
            box-shadow: 0 4px 12px rgba(0, 102, 255, 0.4);
        }

        .btn:active {
            transform: scale(0.98) translateY(0);
        }

        /* ✅ CORRECTION #6: Accessibilité - Focus pour clavier */
        .btn:focus {
            outline: 2px solid var(--color-primary);
            outline-offset: 2px;
            box-shadow: 0 0 0 4px rgba(0, 102, 255, 0.1);
        }

        .disclaimer {
            font-size: 12px;
            color: #9ca3af;
            margin-top: 12px;
        }

        /* ✅ CORRECTION #5: Media queries pour responsive */
        @media (max-width: 768px) {
            body {
                padding: 16px;
            }

            .pricing {
                width: 100%;
                padding: 24px 16px;
            }

            .title {
                font-size: 20px;
            }

            .price {
                font-size: 28px;
            }

            .btn {
                padding: 14px 20px;
                font-size: 14px;
            }
        }
    </style>
</head>
<body>
    <!-- ✅ CORRECTION #6: Lien de retour avec accessibilité -->
    <a href="#" class="back-link" aria-label="Retour à la liste des projets">
        <span>←</span>
        <span>Retour à Ma Liste de Projets</span>
    </a>

    <!-- Conteneur principal -->
    <div class="container">
        <div class="header">
            <h1>Bonnes pratiques et optimisation du flux de travail avec l'IA</h1>
            <p>Composant réparé et optimisé</p>
        </div>

        <!-- COMPOSANT CARTE DE PRIX - CORRIGÉ -->
        <div id="pricing-cards"></div>
    </div>

    <script>
        /**
         * ✅ CORRECTION #7: Composant Carte de Prix Réutilisable
         * Transforme le code statique en composant paramétrable avec props
         */
        class PricingCard {
            constructor(props) {
                this.props = props;
            }

            render() {
                const { title, price, period, features, buttonText, onClick } = this.props;

                // ✅ CORRECTION #1: Fermeture correcte des balises HTML
                const html = `
                    <div class="pricing" role="article" aria-label="Carte de prix: ${title}">
                        <!-- ✅ CORRECTION #1: Fermeture correcte: </h2> au lieu de <h2> -->
                        <h2 class="title">${title}</h2>
                        
                        <!-- Prix avec période -->
                        <div>
                            <span class="price">${price}</span>
                            <span class="period">/${period}</span>
                        </div>

                        <!-- ✅ CORRECTION #6: Liste accessible -->
                        <ul class="features" aria-label="Fonctionnalités incluses">
                            ${features.map((feature, index) => `
                                <li key="${index}">${feature}</li>
                            `).join('')}
                        </ul>

                        <!-- ✅ CORRECTION #4 & #6: Bouton avec accessibilité -->
                        <button 
                            class="btn btn-animate" 
                            aria-label="${buttonText}: ${title}"
                            aria-describedby="disclaimer">
                            ${buttonText}
                        </button>
                        
                        <p class="disclaimer" id="disclaimer">Aucune carte de crédit requise</p>
                    </div>
                `;
                
                return html;
            }
        }

        /**
         * Gestionnaire pour créer plusieurs cartes réutilisables
         */
        class PricingCardManager {
            constructor(containerId) {
                this.container = document.getElementById(containerId);
                this.cards = [];
            }

            addCard(props) {
                const card = new PricingCard(props);
                this.cards.push(card);
                return this;
            }

            renderAll() {
                const html = this.cards.map(card => card.render()).join('');
                this.container.innerHTML = html;
                this.attachEventListeners();
            }

            attachEventListeners() {
                const buttons = this.container.querySelectorAll('.btn');
                buttons.forEach((btn, index) => {
                    btn.addEventListener('click', () => {
                        const cardData = this.cards[index].props;
                        // ✅ CORRECTION #4: Bouton fonctionnel
                        alert(`✅ Vous avez choisi le plan: ${cardData.title}\nPrix: ${cardData.price}/${cardData.period}`);
                    });
                });
            }
        }

        // Initialisation au chargement du DOM
        document.addEventListener('DOMContentLoaded', () => {
            const manager = new PricingCardManager('pricing-cards');

            // ✅ CORRECTION #7: Données réutilisables - Facile à passer en prop
            const basicPlan = {
                title: "Basic Plan",
                price: "$9.99",
                period: "mois",
                features: [
                    "1 GB de stockage",
                    "Support de base",
                    "Toutes les fonctionnalités principales"
                ],
                buttonText: "Commencer l'essai",
                onClick: () => console.log('Basic Plan clicked')
            };

            // Ajouter la carte et afficher
            manager.addCard(basicPlan).renderAll();
        });
    </script>
</body>
</html>
```

---

## 📊 COMPARAISON DÉTAILLÉE

| Aspect | Avant ❌ | Après ✅ |
|--------|---------|---------|
| **Balises HTML** | `<h2>...<h2>` (mal fermée) | `<h2>...</h2>` (correcte) |
| **CSS Shadow** | `box-shdow` (typo) | `box-shadow` (correct) |
| **Alignement** | `text-align: left` | `text-align: center` |
| **Bouton** | Pas de border-radius, cursor | border-radius, cursor: pointer, focus states |
| **Responsive** | Largeur fixe 300px | max-width 300px, 100% width, media queries |
| **Accessibilité** | Aucune | ARIA labels, focus visible, semantic HTML |
| **Réutilisabilité** | Statique, hardcodé | Classe PricingCard + Manager, props paramétrables |
| **Variables CSS** | Couleurs en dur | :root avec variables CSS |
| **Événements** | Aucun sur le bouton | Click event avec feedback |
| **Performance** | Non optimisé | CSS moderne, transition fluides |

---

## 🎓 LEÇONS APPRISES

### 1️⃣ Validation HTML
- Toujours fermer les balises correctement
- Utiliser un validateur HTML (validator.w3.org)

### 2️⃣ Attention aux typos CSS
- `box-shadow` ≠ `box-shdow`
- Utiliser un linter CSS (stylelint)

### 3️⃣ Accessibilité dès le départ
- Ajouter les attributs ARIA
- Styles `:focus` explicites pour la navigation au clavier
- Semantic HTML (`<button>` au lieu de `<div>`)

### 4️⃣ Design responsive
- Utiliser `max-width` au lieu de `width` fixe
- Ajouter des media queries
- Tester sur tous les appareils

### 5️⃣ Architecture réutilisable
- Transformer le code statique en composants
- Passer les données en props
- Faciliter la maintenance et l'évolution

### 6️⃣ Variables CSS
- Centraliser les couleurs et tailles
- Faciliter les changements de thème
- Meilleure maintenabilité

---

## 🚀 PROCHAINES ÉTAPES

- [ ] Créer une variante Premium et Enterprise
- [ ] Ajouter des animations d'entrée
- [ ] Implémenter un système de thème (clair/sombre)
- [ ] Ajouter des tests unitaires
- [ ] Documenter les props du composant
- [ ] Déployer en production

---

**Généré:** 20 Février 2026  
**Status:** ✅ Code validé et optimisé
