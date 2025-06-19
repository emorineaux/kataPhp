
# 📅 Event Planning System — Exercice Technique PHP

Bienvenue dans cet exercice PHP. L'objectif est de construire une API RESTful autour de la gestion d'événements, avec des règles métiers, des statistiques, et des défis techniques progressifs.

---

## 🎯 Objectif

Tu peux choisir de développer ce projet :
- En **PHP pur** (sans framework), avec une architecture propre (POO, router, services, etc.)
- Ou avec un **framework PHP** de ton choix (Symfony, Laravel, Slim, etc.)

Ce test est conçu pour évaluer ta **compréhension métier**, ta **structure de code**, et ta **capacité à résoudre des problèmes concrets**.

---

## 🧩 Étape 1 — API de base : gestion d’événements

Créer une API avec les routes suivantes :

| Méthode | Route         | Description                          |
|--------|----------------|--------------------------------------|
| GET    | /events        | Liste tous les événements            |
| GET    | /events/{id}   | Détails d’un événement               |
| POST   | /events        | Crée un nouvel événement             |
| PUT    | /events/{id}   | Met à jour un événement              |
| DELETE | /events/{id}  | Supprime un événement                |

### Modèle Événement :
- `id` : entier auto-incrémenté
- `name` : string (requis)
- `date` : DateTime (requis)
- `location` : string
- `attendees` : entier (nombre de participants)

---

## 🧩 Étape 2 — Règles métiers

Ajoute une couche de validation avec les règles suivantes :
- ❌ Interdire la création d’un événement dans le passé
- ❌ Interdire un événement avec plus de 500 participants
- ❌ Interdire deux événements au même endroit et à la même date/heure

---

## 🧩 Étape 3 — Statistiques agrégées

Ajouter une route :
```
GET /stats
```
Retourne un objet de statistiques comme :
```json
{
  "total_events": 12,
  "average_attendees": 175.6,
  "events_by_month": {
    "2025-06": 5,
    "2025-07": 7
  }
}
```

---

## 🧩 Étape 4 — Requête complexe

Créer une route :
```
GET /events/search?min_attendees=100&after=2025-07-01
```

Cette route retourne les événements filtrés par :
- Nombre minimum de participants
- Date minimale (événements à venir uniquement)

---

## 🧩 Étape 5 (Bonus) — Planification intelligente

Créer un endpoint :
```
POST /events/schedule
```

Entrée JSON :
```json
{
  "name": "Symfony Meetup",
  "participants": 120,
  "possible_slots": [
    { "date": "2025-07-01 10:00", "location": "Paris" },
    { "date": "2025-07-01 15:00", "location": "Lyon" }
  ]
}
```

Retour attendu :
```json
{
  "chosen_slot": {
    "date": "2025-07-01 15:00",
    "location": "Lyon"
  }
}
```

**But** : choisir le premier créneau disponible sans conflit avec les événements existants.

---

## 🧪 Tests

- Écrire des tests unitaires pour la logique métier
- Tests fonctionnels ou d'intégration si possible
- Exécution des tests via :
```bash
composer test
```

---

## 🔁 CI (GitHub Actions)

Ajouter un fichier `.github/workflows/ci.yml` pour :
- Vérifier la syntaxe PHP
- Valider `composer.json`
- Lancer les tests

---

## 📘 Consignes techniques

- Structure claire
- README complet

---

## ❌ Usage d'outils automatiques

> ⚠️ **L’usage d’outils de génération automatique de code (ChatGPT, Copilot, etc.) est strictement interdit.**  
