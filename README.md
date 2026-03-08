# 💸 Smart Finance Kapu$ta

Aplikacja do zarzadzania domowymi finansami: przychodami, wydatkami, saldem konta, historia transakcji i raportami miesiecznymi.

Projekt sklada sie z frontendu w React oraz backendu API w Express, z baza danych MongoDB (Atlas/lokalnie).

## 🌐 Demo

### 🚀 Wersja online

Aplikacja jest dostepna online pod adresem:

**👉 [https://smart-finance-kapusta.vercel.app/](https://smart-finance-kapusta.vercel.app/)**

**Platformy:**

- **Frontend**: [Vercel](https://vercel.com) - hosting aplikacji React (CRA)
- **Backend**: [Render](https://render.com) - hosting API Express
- **Database**: MongoDB Atlas

**⚠️ Wazne informacje:**

- **Cold Start**: Backend na Render (darmowy plan) moze potrzebowac kilkunastu sekund po dluzszej bezczynnosci.
- **CORS**: Backend akceptuje originy z `FRONTEND_URL` (wspiera tez wildcard `https://*.vercel.app`).

### 📦 Architektura

Aplikacja sklada sie z dwoch czesci:

- **Frontend**: React + Redux Toolkit + React Router, hostowany na Vercel
- **Backend**: Express + Mongoose + JWT auth, hostowany na Render

## 🛠 Uzyte technologie

### Frontend

- **React 18**
- **React Router DOM 7**
- **Redux Toolkit + React Redux**
- **Axios**
- **Chart.js + react-chartjs-2 + chartjs-plugin-datalabels**
- **react-datepicker + moment**
- **CSS Modules**

### Backend

- **Node.js + Express 5**
- **MongoDB + Mongoose**
- **JWT + Passport + passport-jwt**
- **bcryptjs**
- **Joi** (walidacja)
- **cors, dotenv, morgan**

### Narzedzia deweloperskie

- **npm workspaces** (frontend + backend)
- **ESLint (react-scripts)**
- **Git & GitHub**

## 📂 Struktura aplikacji

```
smart-finance/
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   │   ├── Balance/
│   │   │   ├── Expenses/
│   │   │   ├── Income/
│   │   │   ├── CategoryList/
│   │   │   ├── Chart/
│   │   │   ├── DatePickerForm/
│   │   │   ├── LoginForm/
│   │   │   ├── PrivateRoute/
│   │   │   ├── ProtectedRoute/
│   │   │   └── ...
│   │   ├── pages/
│   │   │   ├── LoginPage/
│   │   │   ├── TransactionsPage/
│   │   │   └── ReportsPage/
│   │   ├── hooks/
│   │   ├── redux/
│   │   │   ├── user/
│   │   │   ├── expenses/
│   │   │   ├── incomes/
│   │   │   └── reports/
│   │   ├── App.js
│   │   └── index.js
│   ├── public/
│   ├── .env.example
│   └── package.json
├── backend/
│   ├── auth/
│   ├── controllers/
│   ├── routes/
│   ├── services/
│   ├── models/
│   ├── helpers/
│   ├── .env.example
│   ├── server.js
│   └── package.json
├── render.yaml
└── README.md
```

## 📋 Dostepne strony

- **/** - ekran logowania/rejestracji
- **/transactions/expenses** - lista wydatkow + formularz dodawania
- **/transactions/income** - lista przychodow + formularz dodawania
- **/reports** - raporty z podzialem na kategorie i wykres

## 🚀 Jak uruchomic aplikacje

### Wymagania wstepne

- Node.js (LTS, dla backendu zalecane >= 20.19.0)
- npm

### Instalacja i uruchomienie

1. Sklonuj repozytorium:

   ```bash
   git clone https://github.com/brzozanet/smart-finance.git
   cd smart-finance
   ```

2. Zainstaluj zaleznosci:

   ```bash
   npm install
   ```

3. Skonfiguruj backend:

   ```bash
   cp backend/.env.example backend/.env
   ```

   Przyklad `backend/.env`:

   ```env
   PORT=8000
   DATABASE_URL=mongodb://127.0.0.1:27017/finance_planner
   SECRET=replace_with_long_random_secret
   FRONTEND_URL=http://localhost:3000
   ```

4. Skonfiguruj frontend:

   ```bash
   cp frontend/.env.example frontend/.env
   ```

   Przyklad `frontend/.env`:

   ```env
   REACT_APP_API_URL=http://localhost:8000/
   ```

5. Uruchom aplikacje (frontend + backend):

   ```bash
   npm run dev
   ```

   Frontend: [http://localhost:3000](http://localhost:3000)

## 🌐 API Endpoints

Backend udostepnia nastepujace endpointy:

- `GET /health` - health check API
- `POST /auth/register` - rejestracja uzytkownika
- `POST /auth/login` - logowanie (JWT)
- `POST /auth/logout` - wylogowanie (wymaga auth)
- `PATCH /auth/balance` - aktualizacja salda (wymaga auth)
- `POST /transaction/expense` - dodanie wydatku (wymaga auth)
- `POST /transaction/income` - dodanie przychodu (wymaga auth)
- `DELETE /transaction/:transactionId` - usuniecie transakcji (wymaga auth)
- `GET /transaction/expense` - lista/statystyki wydatkow (wymaga auth)
- `GET /transaction/income` - lista/statystyki przychodow (wymaga auth)

## ✨ Funkcjonalnosci

### Zaimplementowane

- 🔐 Rejestracja i logowanie uzytkownika (JWT)
- 👤 Ochrona tras (`ProtectedRoute`, `PrivateRoute`)
- 💰 Zarzadzanie saldem konta
- 🧾 Dodawanie i usuwanie wydatkow
- 📊 Podsumowania miesieczne (expense/income)
- 🗂 Raporty kategorii + wykres slupkowy
- 📅 Formularz daty (DatePicker) przy dodawaniu transakcji
- 📱 Responsywny interfejs (mobile + desktop)
- ⚠️ Komunikaty bledow walidacji logowania/rejestracji

### Ważne doprecyzowanie stanu projektu

- Backend wspiera operacje dla przychodow i wydatkow.
- W aktualnym frontendzie czesc przychodow/raportow korzysta z danych pomocniczych `redux/fakeDb.js` (do mockowania widokow), podczas gdy wydatki sa zintegrowane z API.

## 📝 Uwagi

- Aplikacja wymaga dzialajacego backendu, aby poprawnie obslugiwac autoryzacje i operacje finansowe.
- W produkcji backend laczy sie z MongoDB Atlas przez `DATABASE_URL`.
- Jesli backend jest usypiany na Render, pierwsze zapytanie moze byc wolniejsze.

### 🌐 Deployment

Projekt jest zdeployowany na:

- **Frontend**: [https://smart-finance-kapusta.vercel.app/](https://smart-finance-kapusta.vercel.app/)
- **Backend**: [https://smart-finance-backend-egfl.onrender.com](https://smart-finance-backend-egfl.onrender.com)

#### Ustawienia produkcyjne ENV

Backend (Render):

```env
PORT=8000
DATABASE_URL=mongodb+srv://<DB_USER>:<DB_PASS>@<CLUSTER_HOST>/<DB_NAME>?retryWrites=true&w=majority
SECRET=<LONG_RANDOM_SECRET>
FRONTEND_URL=https://smart-finance-kapusta.vercel.app,https://*.vercel.app
```

Frontend (Vercel):

```env
REACT_APP_API_URL=https://smart-finance-backend-egfl.onrender.com/
```

## 🎯 Status projektu

✅ Projekt dziala na produkcji (Vercel + Render).

🛠 Trwa dalsze porzadkowanie warstwy danych na froncie (pelna unifikacja API dla raportow i przychodow).

---

**Smart Finance Kapu$ta to praktyczny projekt full-stack do zarzadzania domowym budzetem z autoryzacja, API i baza MongoDB.**
