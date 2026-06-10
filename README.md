# NoteHub - Note Management Application

A modern note management application built with Next.js, Zustand, and React Query. Features a clean UI with advanced filtering, search capabilities, and real-time state management.

## Features

- 📝 **Create, Read, Update, Delete Notes** - Full CRUD operations for note management
- 🔍 **Advanced Search** - Debounced search functionality to find notes quickly
- 🏷️ **Filtering** - Filter notes by status and other criteria
- 📄 **Pagination** - Efficient note browsing with pagination controls
- 🎨 **Modal Preview** - Preview notes in an elegant modal dialog
- 🔔 **Toast Notifications** - Real-time feedback for user actions
- ⚡ **State Management** - Zustand-based global state with React Query integration
- 📱 **Responsive Design** - Works seamlessly on desktop and mobile devices
- 🚀 **Server-Side Integration** - API-driven architecture with axios

## Tech Stack

- **Framework**: [Next.js 16](https://nextjs.org/) - React framework with App Router
- **State Management**: [Zustand 5](https://zustand-demo.pmnd.rs/) - Lightweight state management
- **Data Fetching**: [TanStack React Query 5](https://tanstack.com/query/latest) - Server state management
- **HTTP Client**: [Axios](https://axios-http.com/) - Promise-based HTTP client
- **Notifications**: [React Hot Toast](https://react-hot-toast.com/) - Lightweight toast notifications
- **Pagination**: [React Paginate](https://github.com/AdeleD/react-paginate) - Pagination component
- **Utilities**: [use-debounce](https://www.npmjs.com/package/use-debounce) - Debounce hook
- **Language**: TypeScript - For type safety
- **Styling**: CSS Modules - Component-scoped styling

## Getting Started

### Prerequisites

- Node.js 18+
- npm or yarn package manager

### Installation

1. Clone the repository
```bash
git clone <repository-url>
cd 08-zustand
```

2. Install dependencies
```bash
npm install
# or
yarn install
```

3. Set up environment variables (if needed)
```bash
# Create a .env.local file
# Add your API endpoint
NEXT_PUBLIC_API_URL=your_api_url_here
```

### Running the Development Server

```bash
npm run dev
# or
yarn dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser to see the application.

The app auto-reloads as you make changes to the code.

### Building for Production

```bash
npm run build
npm run start
```

## Project Structure

```
app/                          # Next.js App Router
├── layout.tsx               # Root layout
├── page.tsx                 # Home page
├── loading.tsx              # Loading UI
├── not-found.tsx            # 404 page
├── @modal/                  # Modal slot for parallel routes
│   ├── (.)notes/[id]/       # Modal note preview
│   └── default.tsx
├── notes/                   # Notes section
│   ├── [id]/                # Individual note details
│   ├── action/create/       # Note creation page
│   └── filter/              # Filtered notes listing
│       ├── [...slug]/       # Dynamic filter routes
│       └── @sidebar/        # Sidebar slot
└── globals.css              # Global styles

components/                   # Reusable React components
├── Footer/                  # Footer component
├── Header/                  # Header navigation
├── Modal/                   # Modal wrapper
├── NoteForm/                # Note creation/edit form
├── NoteList/                # Notes list display
├── Pagination/              # Pagination controls
├── SearchBox/               # Search input
└── TanStackProvider/        # React Query provider

lib/                          # Utility functions and store
├── api.ts                   # API integration layer
└── store/
    └── noteStore.ts         # Zustand store for notes

types/                        # TypeScript type definitions
└── note.ts                  # Note type definitions
```

## State Management

### Zustand Store

The application uses Zustand for global state management. The note store (`lib/store/noteStore.ts`) manages:

- Notes list
- Currently selected note
- Filter and search parameters
- Loading and error states

```typescript
// Example: Using the note store
import { useNoteStore } from '@/lib/store/noteStore';

const MyComponent = () => {
  const notes = useNoteStore((state) => state.notes);
  const addNote = useNoteStore((state) => state.addNote);

  return (
    // Component JSX
  );
};
```

### React Query Integration

React Query handles server-side state and caching through the `TanStackProvider` component. This ensures:

- Efficient data fetching and caching
- Automatic background updates
- Built-in error handling and retry logic

## API Integration

The `lib/api.ts` file contains the API client configuration using Axios. All API calls go through this centralized layer for:

- Consistent error handling
- Request/response interceptors
- Base URL configuration

## Usage Examples

### Creating a Note

1. Navigate to the "Create Note" page
2. Fill in the note form
3. Submit to save the note
4. Toast notification confirms creation

### Searching Notes

1. Use the search box in the header
2. Type your search query (debounced for performance)
3. Results update automatically

### Filtering Notes

1. Navigate to the filter section
2. Select desired filter criteria
3. View filtered results with pagination

### Previewing a Note

1. Click on any note in the list
2. Modal dialog opens with note preview
3. View full note details without leaving the page

## Available Scripts

- `npm run dev` - Start development server
- `npm run build` - Build for production
- `npm run start` - Start production server
- `npm run lint` - Run ESLint

## Performance Optimizations

- **Debounced Search** - Reduces API calls during typing
- **React Query Caching** - Minimizes redundant server requests
- **Code Splitting** - Automatic with Next.js App Router
- **CSS Modules** - Scoped styling prevents conflicts
- **Server Components** - Default in App Router for better performance

## Browser Support

- Chrome (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)

## Contributing

Feel free to submit issues and enhancement requests!

## License

This project is part of the GoIt curriculum.
