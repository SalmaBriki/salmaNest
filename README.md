# salmaNest — API NestJS (employés, utilisateurs, chat)

API REST construite avec **NestJS**, **TypeORM** et **MongoDB**, avec un chat en temps réel via **Socket.IO**.

## Fonctionnalités

- **Employés** (`/employee`) : CRUD complet, calcul des heures travaillées (`/:id/worked-hours`), du salaire (`/:id/salary`) et de l'impôt (`/:id/tax`)
- **Utilisateurs** (`/user`) : création, activation de compte, recherche par id ou par e-mail, liste des comptes actifs
- **Chat** : passerelle WebSocket (événement `send_message`) avec messages persistés en base
- Validation des entrées (`class-validator`, `ValidationPipe` global)

## Stack

NestJS 11 · TypeORM · MongoDB · Socket.IO · Jest

## Lancer le projet

Prérequis : Node.js et une instance MongoDB.

```bash
npm install

# optionnel : sinon mongodb://localhost:27017/atelier-typeorm
export DATABASE_URL="mongodb://localhost:27017/ma-base"

npm run start:dev   # http://localhost:3000
npm test
```

## Structure

```
src/
├── employee/   # contrôleur, service, entité, DTO
├── user/       # contrôleur, service, entité, DTO
├── messages/   # entité, service, chat.gateway.ts (WebSocket)
├── config/     # configuration TypeORM
└── main.ts
```

## Points à améliorer

- Hasher les mots de passe (bcrypt) au lieu de les comparer en clair
- Désactiver `synchronize` en production
- Documenter l'API avec Swagger
