# Fraud Guard AI

A complete credit card fraud detection system using machine learning with a React frontend and FastAPI backend.

## Quick Start

### 1. Train the Model (First Time)
```bash
cd backend/workspace
# Run the notebook to train and save the model
jupyter notebook notebook.ipynb
```

### 2. Start Backend
```bash
cd backend
./start.sh
# Backend runs on http://localhost:8000
```

### 3. Start Frontend
```bash
npm install && npm run dev
# Frontend runs on http://localhost:5173
```

## Project Structure

```
fraud-guard-ai/
├── backend/                 # FastAPI backend
│   ├── main.py             # Main API application
│   ├── requirements.txt    # Python dependencies
│   ├── start.sh           # Startup script
│   └── workspace/         # Model files and data
├── src/pages/             # React frontend pages
│   ├── PredictionForm.tsx     # Transaction input form
│   └── PredictionResult.tsx   # Fraud prediction results
└── package.json           # Frontend dependencies
```

## Features

### CSV Data Structure
```
trans_date_trans_time,merchant,category,amt,city,state,lat,long,city_pop,job,dob,trans_num,merch_lat,merch_long,is_fraud
```

### API Endpoints
- `POST /predict` - Fraud prediction
- `GET /health` - Health check
- `GET /docs` - API documentation

### ML Model
- Random Forest/XGBoost with 99%+ accuracy
- Real-time prediction pipeline
- 18+ engineered features
- SMOTE-balanced training data

## Expanding the ESLint configuration

If you are developing a production application, we recommend updating the configuration to enable type-aware lint rules:

```js
export default tseslint.config([
  globalIgnores(['dist']),
  {
    files: ['**/*.{ts,tsx}'],
    extends: [
      // Other configs...

      // Remove tseslint.configs.recommended and replace with this
      ...tseslint.configs.recommendedTypeChecked,
      // Alternatively, use this for stricter rules
      ...tseslint.configs.strictTypeChecked,
      // Optionally, add this for stylistic rules
      ...tseslint.configs.stylisticTypeChecked,

      // Other configs...
    ],
    languageOptions: {
      parserOptions: {
        project: ['./tsconfig.node.json', './tsconfig.app.json'],
        tsconfigRootDir: import.meta.dirname,
      },
      // other options...
    },
  },
])
```

You can also install [eslint-plugin-react-x](https://github.com/Rel1cx/eslint-react/tree/main/packages/plugins/eslint-plugin-react-x) and [eslint-plugin-react-dom](https://github.com/Rel1cx/eslint-react/tree/main/packages/plugins/eslint-plugin-react-dom) for React-specific lint rules:

```js
// eslint.config.js
import reactX from 'eslint-plugin-react-x'
import reactDom from 'eslint-plugin-react-dom'

export default tseslint.config([
  globalIgnores(['dist']),
  {
    files: ['**/*.{ts,tsx}'],
    extends: [
      // Other configs...
      // Enable lint rules for React
      reactX.configs['recommended-typescript'],
      // Enable lint rules for React DOM
      reactDom.configs.recommended,
    ],
    languageOptions: {
      parserOptions: {
        project: ['./tsconfig.node.json', './tsconfig.app.json'],
        tsconfigRootDir: import.meta.dirname,
      },
      // other options...
    },
  },
])
```
