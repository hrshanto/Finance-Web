# FinanceFlow - Personal Finance Tracker

A premium modern personal finance and daily expense tracking web application with a beautiful dark UI and full admin dashboard.

## Features

### Dashboard
- Total balance card with real-time updates
- Daily expense summary
- Monthly income/expense overview
- Interactive charts with animated transitions
- Recent transactions with quick actions

### Transaction Management
- Add income and expense entries
- Edit and delete transactions
- Category-based organization
- Notes and date tracking
- Search and filter by date, type, and category
- CSV export functionality

### Categories
- Pre-built expense categories (Food, Shopping, Ads, Forex, Bills, Personal, etc.)
- Pre-built income categories (Salary, Freelance, Investments, etc.)
- Custom category creation with color picker
- Edit and delete categories

### Analytics
- Daily spending patterns over 14 days
- Monthly trends over 12 months
- Expense breakdown by category with pie charts
- Spending by day of the week
- Smart insights and recommendations
- Savings rate tracking

### Settings
- Profile information
- Currency selection (7 major currencies)
- Monthly budget setting
- Notification preferences
- Password change
- Data export (JSON backup)
- Account deletion

## Tech Stack

- **Frontend**: Next.js 13, React 18, TypeScript
- **Styling**: Tailwind CSS with custom dark theme
- **UI Components**: shadcn/ui
- **Animations**: Framer Motion
- **Charts**: Recharts
- **Backend**: Supabase (PostgreSQL + Auth)
- **Authentication**: Supabase Auth with email/password

## Getting Started

### Prerequisites
- Node.js 18+ 
- A Supabase account

### Environment Setup

Create a `.env.local` file in the root directory:

```env
NEXT_PUBLIC_SUPABASE_URL=your_supabase_url
NEXT_PUBLIC_SUPABASE_ANON_KEY=your_supabase_anon_key
```

### Installation

```bash
npm install
npm run dev
```

The application will be available at `http://localhost:3000`

## Database Schema

The application uses three main tables:

### Categories
- `id`: UUID (primary key)
- `user_id`: UUID (foreign key to auth.users)
- `name`: Text
- `type`: 'income' | 'expense'
- `icon`: Text
- `color`: Text
- `is_default`: Boolean

### Transactions
- `id`: UUID (primary key)
- `user_id`: UUID (foreign key to auth.users)
- `category_id`: UUID (foreign key to categories)
- `amount`: Decimal
- `type`: 'income' | 'expense'
- `description`: Text
- `notes`: Text
- `transaction_date`: Date
- `created_at`: Timestamp
- `updated_at`: Timestamp

### User Settings
- `id`: UUID (primary key)
- `user_id`: UUID (foreign key to auth.users)
- `currency`: Text
- `currency_symbol`: Text
- `theme`: Text
- `monthly_budget`: Decimal
- `notifications_enabled`: Boolean

## Security

- Row Level Security (RLS) enabled on all tables
- Users can only access their own data
- Secure authentication with Supabase Auth
- Protected dashboard routes
- Input validation on all forms

## Project Structure

```
app/
├── dashboard/
│   ├── page.tsx          # Main dashboard
│   ├── layout.tsx       # Dashboard layout with sidebar
│   ├── transactions/    # Transaction management
│   ├── categories/      # Category management
│   ├── analytics/       # Analytics & insights
│   └── settings/        # User settings
├── login/
│   └── page.tsx         # Login/Signup page
├── layout.tsx           # Root layout
├── page.tsx             # Redirect page
└── globals.css          # Global styles

components/
├── layout/
│   └── Sidebar.tsx      # Navigation sidebar
└── ui/                  # shadcn/ui components

contexts/
└── AuthContext.tsx      # Authentication state

lib/
├── supabase.ts          # Supabase client & types
├── hooks.tsx            # Custom hooks
└── utils.ts             # Utility functions
```

## Deployment

### Vercel (Recommended)

1. Push your code to GitHub
2. Connect your repository to Vercel
3. Add environment variables in Vercel dashboard
4. Deploy

### Netlify

The project includes a `netlify.toml` configuration file for easy deployment.

## Default Categories

### Expense Categories
- Food, Shopping, Ads, Forex, Bills, Personal, Transport, Entertainment, Healthcare, Education

### Income Categories
- Salary, Freelance, Investments, Other Income

## License

This project is private and for personal use.
