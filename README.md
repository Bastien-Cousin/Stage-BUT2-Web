# ✍️ Ingrid Sardou — Site Web vitrine, réservation en ligne & administration

Application web professionnelle conçue et développée dans le cadre de mon **stage de deuxième année de BUT Informatique** pour **Ingrid Sardou, graphopédagogue indépendante**.

Le projet combine un **site vitrine responsive**, un système complet de **prise de rendez-vous en ligne** et une **interface d'administration** permettant de gérer l'activité et différents contenus du site.

🌐 **Site en production :** [ingridsardou.fr](https://ingridsardou.fr)

![Next.js](https://img.shields.io/badge/Next.js-000000?style=for-the-badge&logo=nextdotjs&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)
![Prisma](https://img.shields.io/badge/Prisma-2D3748?style=for-the-badge&logo=prisma&logoColor=white)
![Supabase](https://img.shields.io/badge/Supabase-3FCF8E?style=for-the-badge&logo=supabase&logoColor=white)
![Upstash](https://img.shields.io/badge/Upstash-00E9A3?style=for-the-badge&logo=upstash&logoColor=000000)
![Vercel](https://img.shields.io/badge/Vercel-000000?style=for-the-badge&logo=vercel&logoColor=white)

> **À propos de ce dépôt**
>
> Ce dépôt public constitue une **présentation technique du projet**.  
> Le code source complet n'est volontairement pas publié afin de respecter le contexte professionnel dans lequel l'application a été développée.

---

## 🎯 Objectifs du projet

L'objectif était de concevoir une solution web complète permettant à une professionnelle de la graphopédagogie de présenter son activité tout en permettant la gestion de ses rendez-vous.

Le projet devait répondre à plusieurs besoins :

- présenter clairement l'activité, les prestations et les informations utiles ;
- permettre aux visiteurs de prendre rendez-vous directement en ligne ;
- centraliser la gestion des rendez-vous et des disponibilités ;
- permettre de modifier différents contenus du site sans intervenir directement dans le code ;
- proposer une expérience responsive adaptée aux ordinateurs et appareils mobiles ;
- assurer la mise en production, la sécurité et le référencement du site.

Le projet a été conçu pour être réellement utilisé en production après la fin du stage.

---

## 🌐 Partie publique

Le site propose plusieurs espaces destinés aux visiteurs.

### 🏠 Site vitrine

La partie publique présente notamment :

- l'activité de graphopédagogie ;
- les prestations proposées ;
- les différents types de séances ;
- les tarifs et informations utiles ;
- les coordonnées de contact ;
- différentes ressources autour de l'écriture.

L'interface a été conçue avec **Next.js, React, TypeScript et Tailwind CSS** afin d'obtenir un site moderne et responsive.

### 📅 Prise de rendez-vous

Le site intègre un parcours de réservation permettant à un visiteur de prendre rendez-vous directement depuis l'application.

Le parcours repose principalement sur les étapes suivantes :

1. sélection d'une prestation ;
2. sélection du type de séance correspondant ;
3. choix d'une date disponible ;
4. choix d'un créneau horaire ;
5. saisie des coordonnées du client ;
6. vérification et confirmation du rendez-vous.

Les disponibilités proposées sont générées à partir de la configuration définie depuis l'espace d'administration.

Avant l'enregistrement définitif, les données sont de nouveau contrôlées côté serveur afin d'éviter notamment les réservations sur des créneaux devenus indisponibles.

### 📩 Contact

Un formulaire permet aux visiteurs de contacter directement la professionnelle depuis le site.

Les messages sont transmis par email à l'aide de **Resend**.

### 📚 Boîte à outils

Le site propose également une section regroupant différentes ressources au format PDF.

Ces documents peuvent être consultés ou téléchargés par les visiteurs.

### 🗺️ Réseau et carte interactive

Une partie du site permet également de présenter différents cabinets et professionnels du réseau à travers une organisation géographique et une carte interactive.

### ⚖️ Informations légales

Le site comprend les pages nécessaires concernant notamment :

- les mentions légales ;
- la confidentialité ;
- la gestion des données personnelles.

---

## 🔐 Interface d'administration

Une interface dédiée permet à la professionnelle de gérer son activité directement depuis le site.

L'accès à cet espace est protégé par authentification.

### 📆 Gestion des rendez-vous

L'administration permet notamment de :

- consulter les rendez-vous par journée ;
- visualiser les informations associées à un rendez-vous ;
- modifier un rendez-vous existant ;
- annuler un rendez-vous ;
- consulter les coordonnées nécessaires à la prise en charge du client.

Les informations personnelles associées aux rendez-vous ne sont accessibles que depuis la partie protégée de l'application.

### 🕐 Gestion des disponibilités

L'administratrice peut configurer les créneaux proposés lors de la réservation.

Elle peut notamment gérer :

- les horaires disponibles ;
- les créneaux de rendez-vous ;
- les jours non disponibles ;
- les périodes d'absence ou de vacances ;
- les blocages ponctuels de certains créneaux.

Le système de réservation utilise ensuite cette configuration pour déterminer les disponibilités réellement proposées aux visiteurs.

### 🧩 Prestations et types de rendez-vous

Les prestations ne sont pas codées directement dans les pages du site.

L'administration permet de gérer les différents services proposés ainsi que les types de séances qui leur sont associés.

Cette organisation permet de faire évoluer l'offre sans devoir modifier le fonctionnement général de l'application.

### ⚙️ Personnalisation du site

Différents éléments du site peuvent également être configurés depuis l'administration, par exemple :

- certaines informations de contact ;
- différents contenus textuels ;
- les prestations proposées ;
- certaines informations affichées sur le site ;
- différentes ressources mises à disposition des visiteurs.

L'objectif était de rendre le site suffisamment autonome pour que les modifications courantes ne nécessitent pas systématiquement une intervention dans le code source.

---

## 🧱 Architecture technique

Le projet utilise **Next.js comme framework full-stack**.

Le front-end et les fonctionnalités serveur sont donc regroupés au sein d'une même application, tout en communiquant avec plusieurs services externes.

```text
                 ┌───────────────────────┐
                 │      Utilisateur      │
                 │                       │
                 │ Visiteur / Admin      │
                 └───────────┬───────────┘
                             │ HTTPS
                             ▼
                 ┌───────────────────────┐
                 │        Next.js        │
                 │                       │
                 │ React + TypeScript    │
                 │ Tailwind CSS          │
                 │ Pages & API           │
                 └───────┬─────┬─────────┘
                         │     │
             ┌───────────┘     └──────────────┐
             ▼                                ▼
┌────────────────────────┐       ┌────────────────────────┐
│     Prisma ORM         │       │     Upstash Redis      │
│                        │       │                        │
│ Accès et validation    │       │ Rate limiting /        │
│ des données            │       │ protection des routes  │
└───────────┬────────────┘       └────────────────────────┘
            │
            ▼
┌────────────────────────┐
│      PostgreSQL        │
│      Supabase          │
│                        │
│ RDV, créneaux,         │
│ services, paramètres…  │
└────────────────────────┘


                 Next.js
                    │
                    ▼
          ┌─────────────────────┐
          │       Resend        │
          │                     │
          │ Emails de contact   │
          │ et notifications    │
          └─────────────────────┘
```

---

## 🗄️ Gestion des données

Le projet repose sur une base de données relationnelle **PostgreSQL**, manipulée depuis l'application avec **Prisma ORM**.

Les principales données concernent notamment :

- les rendez-vous ;
- les coordonnées associées aux réservations ;
- les créneaux horaires ;
- les disponibilités ;
- les prestations ;
- les différents types de séances ;
- les périodes bloquées ;
- les paramètres et contenus configurables du site ;
- les différentes ressources administrables.

Prisma permet également de gérer le schéma de données et les migrations tout au long du développement.

---

## 🛡️ Sécurité

La sécurité était particulièrement importante puisque l'application manipule des informations personnelles liées aux rendez-vous et dispose d'une interface d'administration.

Plusieurs mécanismes ont été mis en place.

### Authentification administrateur

L'accès à l'administration repose notamment sur :

- un mot de passe stocké sous forme de hash avec **bcrypt** ;
- une authentification basée sur **JWT** ;
- un token conservé dans un **cookie HTTP-only** ;
- une protection des pages et endpoints réservés à l'administration.

### Protection des endpoints

Les routes sensibles disposent également de contrôles côté serveur afin de vérifier les autorisations avant toute manipulation des données.

### Rate limiting

**Upstash Redis** est utilisé pour limiter le nombre de requêtes sur certaines fonctionnalités sensibles.

Ce mécanisme permet notamment de réduire les risques :

- de spam ;
- d'abus des formulaires ;
- de tentatives répétées sur certains endpoints.

### Validation des données

Les informations reçues par le serveur sont contrôlées avant leur enregistrement.

Le système de réservation vérifie également qu'un créneau est toujours disponible au moment où le rendez-vous est réellement créé.

### Données privées

Les informations personnelles fournies lors d'une réservation ne sont pas affichées publiquement et sont réservées aux fonctionnalités nécessaires à la gestion des rendez-vous.

Les secrets et identifiants utilisés par les différents services sont stockés dans des variables d'environnement et ne sont pas intégrés directement au code.

---

## 📧 Emails transactionnels

**Resend** est utilisé pour les fonctionnalités nécessitant l'envoi d'emails.

Il intervient notamment pour :

- le formulaire de contact ;
- les notifications associées aux prises de rendez-vous.

Cette intégration permet de gérer les emails côté serveur sans exposer de clé d'API dans le navigateur.

---

## 🔎 Référencement

Une attention particulière a été portée au référencement naturel du site.

Le projet comprend notamment :

- des métadonnées adaptées aux différentes pages ;
- un `sitemap` ;
- une structure HTML adaptée au référencement ;
- des pages accessibles directement par URL ;
- une conception responsive.

L'utilisation de **Next.js** permet également de bénéficier de fonctionnalités adaptées au rendu côté serveur et au référencement.

---

## 📊 Analytics

Le site utilise **Vercel Analytics** afin de disposer d'indicateurs sur son utilisation et sa fréquentation.

Cela permet de suivre l'activité du site depuis l'environnement Vercel sans intégrer un système complet d'analyse directement dans l'application.

---

## 🚀 Mise en production

L'application est déployée sur **Vercel**.

Le nom de domaine **ingridsardou.fr** est géré depuis **OVH** et relié au déploiement Vercel.

L'environnement de production comprend notamment :

```text
Application       → Vercel
Nom de domaine    → OVH
Base de données   → PostgreSQL / Supabase
ORM               → Prisma
Rate limiting     → Upstash Redis
Emails            → Resend
Analytics         → Vercel Analytics
```

Le site bénéficie également d'un accès HTTPS en production.

---

## 🛠️ Technologies utilisées

### Développement

- **Next.js** — framework principal de l'application
- **React** — construction des interfaces
- **TypeScript** — développement typé du projet
- **Tailwind CSS** — mise en forme et responsive design
- **PostgreSQL** — base de données relationnelle
- **Prisma** — ORM et gestion du schéma de données
- **Supabase** — infrastructure liée aux données
- **Upstash Redis** — rate limiting
- **Resend** — envoi d'emails transactionnels

### Déploiement et services

- **Vercel** — hébergement et déploiement
- **OVH** — gestion du nom de domaine
- **Vercel Analytics** — statistiques de fréquentation

### Conception et organisation

- **Figma** — conception des maquettes et de l'interface
- **Looping** — modélisation de la base de données
- **Trello** — organisation et suivi du projet
- **Git / GitHub** — versionnement du code source

---

## 🎨 Conception du projet

Le projet a été développé à partir d'un besoin réel exprimé par la professionnelle.

Le travail a couvert l'ensemble du cycle de création de l'application :

1. analyse des besoins ;
2. définition des fonctionnalités ;
3. organisation du projet ;
4. création des maquettes avec Figma ;
5. modélisation de la base de données ;
6. choix de l'architecture technique ;
7. développement du front-end ;
8. développement des fonctionnalités serveur ;
9. création de l'administration ;
10. sécurisation de l'application ;
11. tests et corrections ;
12. configuration du domaine ;
13. déploiement en production.

Les fonctionnalités ont évolué au cours du stage en fonction des retours et des besoins de la professionnelle.

---

## 💼 Contexte professionnel

Ce projet a été réalisé **individuellement côté technique** durant mon stage de deuxième année de BUT Informatique.

La professionnelle à l'origine du projet définissait les besoins métier, fournissait les différents contenus nécessaires et validait les choix réalisés au cours du développement.

J'ai pris en charge les différentes étapes techniques du projet, notamment :

- l'analyse et la conception de la solution ;
- la création des maquettes ;
- la modélisation de la base de données ;
- le choix de la stack technique ;
- le développement de l'interface publique ;
- le développement du système de réservation ;
- le développement de l'interface d'administration ;
- la gestion de la base de données ;
- la sécurisation de l'application ;
- l'intégration des différents services externes ;
- le référencement ;
- la configuration du domaine ;
- le déploiement et la mise en production.

Ce projet m'a permis de travailler sur une application destinée à un **véritable environnement de production**, avec des problématiques qui dépassent le simple développement d'une interface : sécurité, données personnelles, autonomie de l'administratrice, déploiement, référencement et maintenance.

---

## 🔒 Code source

Ce dépôt est volontairement consacré à la **présentation du projet**.

Le code source complet, la configuration de production ainsi que les informations internes ne sont pas publiés afin de respecter le cadre professionnel du projet et les données associées à son exploitation.

Le dépôt a pour objectif de présenter :

- les fonctionnalités développées ;
- les choix techniques ;
- l'architecture générale ;
- les problématiques rencontrées ;
- les compétences mises en œuvre.

---

## 📅 Réalisation

**Avril – juin 2026** — Stage de deuxième année de BUT Informatique, environ **9 semaines**.
