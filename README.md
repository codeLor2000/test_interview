This is a [Next.js](https://nextjs.org) project bootstrapped with [`create-next-app`](https://nextjs.org/docs/app/api-reference/cli/create-next-app).

## Getting Started

First, run the development server:

```bash
npm run dev
# or
yarn dev
# or
pnpm dev
# or
bun dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

You can start editing the page by modifying `app/page.tsx`. The page auto-updates as you edit the file.

This project uses [`next/font`](https://nextjs.org/docs/app/building-your-application/optimizing/fonts) to automatically optimize and load [Geist](https://vercel.com/font), a new font family for Vercel.

## Learn More

To learn more about Next.js, take a look at the following resources:

- [Next.js Documentation](https://nextjs.org/docs) - learn about Next.js features and API.
- [Learn Next.js](https://nextjs.org/learn) - an interactive Next.js tutorial.

You can check out [the Next.js GitHub repository](https://github.com/vercel/next.js) - your feedback and contributions are welcome!

## Deploy on Vercel

The easiest way to deploy your Next.js app is to use the [Vercel Platform](https://vercel.com/new?utm_medium=default-template&filter=next.js&utm_source=create-next-app&utm_campaign=create-next-app-readme) from the creators of Next.js.

Check out our [Next.js deployment documentation](https://nextjs.org/docs/app/building-your-application/deploying) for more details.
//--------------



# SUNFIL E-commerce - Frontend Test Interview

## 📋 Giới thiệu dự án

Đây là một dự án test interview frontend được xây dựng dựa trên design của website SUNFIL - chuyên cung cấp bộ lọc ô tô. Dự án được phát triển với mục tiêu thể hiện khả năng triển khai giao diện hiện đại, clean code và tư duy xử lý UX/UI.

## 🎯 Mục tiêu dự án

- **Code sạch, rõ ràng, có khả năng tái sử dụng**
- **Giao diện mới mẻ, theo xu hướng, thân thiện, dễ sử dụng**
- **Có thể kết hợp với API thật trong tương lai**
- **Tuân thủ cấu trúc code logic, dễ đọc, dễ bảo trì**
- **Ưu tiên khả năng trình bày tư duy trong việc triển khai giao diện, xử lý trạng thái dữ liệu, UX tương tác**

## 🛠️ Tech Stack

### Frontend Framework
- **Next.js 15** - React framework với App Router
- **TypeScript** - Type safety và better developer experience
- **Tailwind CSS** - Utility-first CSS framework

### UI Components
- **shadcn/ui** - High-quality, accessible UI components
- **Lucide React** - Beautiful & consistent icon library
- **Radix UI** - Unstyled, accessible components

### State Management
- **React Context** - Global state management
- **Custom Hooks** - Reusable logic abstraction

## 🏗️ Kiến trúc dự án

```
src/
├── app/                    # Next.js App Router
│   ├── layout.tsx         # Root layout
│   └── page.tsx           # Homepage
├── components/
│   ├── layout/            # Layout components
│   │   ├── header.tsx     # Main navigation
│   │   ├── sidebar.tsx    # Filter sidebar
│   │   └── footer.tsx     # Footer with company info
│   ├── sections/          # Page sections
│   │   ├── promo-banner.tsx    # Hero promotional banner
│   │   ├── featured-products.tsx # Featured products grid
│   │   └── product-grid.tsx     # Main products listing
│   └── ui/                # Reusable UI components
│       └── product-card.tsx     # Product display card
├── contexts/              # React Context providers
│   └── product-context.tsx     # Product filtering state
├── hooks/                 # Custom React hooks
│   └── use-cart.ts       # Shopping cart logic
├── types/                 # TypeScript type definitions
│   └── product.ts        # Product & filter interfaces
└── lib/                  # Utility functions
    └── utils.ts          # Helper functions
```

## ✨ Tính năng chính

### 🎨 Giao diện người dùng
- **Responsive Design**: Tối ưu cho mọi thiết bị (mobile, tablet, desktop)
- **Modern UI**: Design hiện đại với Tailwind CSS
- **Interactive Elements**: Hover effects, transitions, micro-animations
- **Accessibility**: Tuân thủ WCAG guidelines

### 🔍 Tính năng sản phẩm
- **Product Grid**: Hiển thị sản phẩm dạng grid/list
- **Featured Products**: Section sản phẩm nổi bật
- **Product Filtering**: Lọc theo danh mục, thương hiệu, giá
- **Product Search**: Tìm kiếm sản phẩm (ready for API)
- **Sort Options**: Sắp xếp theo giá, rating, mới nhất

### 🛒 Tương tác người dùng
- **Wishlist**: Thêm/xóa sản phẩm yêu thích
- **Shopping Cart**: Quản lý giỏ hàng (ready for implementation)
- **Product Quick View**: Xem nhanh thông tin sản phẩm
- **Rating System**: Hiển thị đánh giá sao

## 🎯 Highlights kỹ thuật

### 1. Clean Architecture
```typescript
// Component tách biệt logic và UI
const ProductCard = ({ product, viewMode, variant }) => {
  // UI logic
  const [isWishlisted, setIsWishlisted] = useState(false)
  
  // Business logic
  const formatPrice = useCallback((price) => {
    return new Intl.NumberFormat('vi-VN', {
      style: 'currency',
      currency: 'VND'
    }).format(price)
  }, [])
  
  // Render logic
  return (/* JSX */)
}
```

### 2. Context Pattern cho State Management
```typescript
// Global state với TypeScript
interface ProductContextType {
  filters: ProductFilters
  updateFilters: (filters: Partial<ProductFilters>) => void
  resetFilters: () => void
}

// Provider pattern
export function ProductProvider({ children }: { children: ReactNode }) {
  const [filters, setFilters] = useState<ProductFilters>(defaultFilters)
  // ... logic
  return <ProductContext.Provider value={value}>{children}</ProductContext.Provider>
}
```

### 3. Custom Hooks cho Reusability
```typescript
// Tái sử dụng logic giỏ hàng
export function useCart() {
  const [items, setItems] = useState<CartItem[]>([])
  
  const addToCart = useCallback((product: Product, quantity = 1) => {
    // Logic thêm sản phẩm
  }, [])
  
  return { items, addToCart, removeFromCart, totalPrice }
}
```

### 4. TypeScript cho Type Safety
```typescript
// Định nghĩa types rõ ràng
interface Product {
  id: string
  name: string
  price: number
  originalPrice: number
  image: string
  rating: number
  category: string
  brand: string
  isHot: boolean
  isBestSeller: boolean
}
```

## 🚀 Performance Optimizations

### 1. React Optimizations
- **useMemo**: Memoize expensive calculations (filtering, sorting)
- **useCallback**: Prevent unnecessary re-renders
- **Lazy Loading**: Code splitting cho components lớn

### 2. Next.js Features
- **Image Optimization**: Next.js Image component
- **Static Generation**: Pre-render pages khi có thể
- **Bundle Optimization**: Automatic code splitting

### 3. UX Optimizations
- **Skeleton Loading**: Loading states cho better UX
- **Optimistic Updates**: Immediate UI feedback
- **Error Boundaries**: Graceful error handling

## 🎨 Design System

### Color Palette
```css
/* Primary Colors */
--blue-primary: #1E40AF    /* Main brand color */
--blue-secondary: #3B82F6  /* Secondary actions */
--orange-accent: #F97316   /* Call-to-action */
--red-price: #DC2626       /* Price highlighting */

/* Neutral Colors */
--gray-50: #F9FAFB         /* Background */
--gray-100: #F3F4F6        /* Light background */
--gray-900: #111827        /* Text primary */
```

### Typography Scale
- **Headings**: font-bold, responsive sizes
- **Body**: font-medium, readable line-height
- **Captions**: font-normal, smaller sizes

### Spacing System
- **Consistent spacing**: 4px base unit
- **Component padding**: 12px, 16px, 24px
- **Section margins**: 32px, 48px, 64px

## 📱 Responsive Design

### Breakpoints
```css
/* Mobile First Approach */
sm: 640px   /* Small devices */
md: 768px   /* Medium devices */
lg: 1024px  /* Large devices */
xl: 1280px  /* Extra large devices */
```

### Grid System
- **Mobile**: 1 column layout
- **Tablet**: 2-3 columns
- **Desktop**: 4-5 columns
- **Sidebar**: Responsive collapse

## 🔮 Future Enhancements

### API Integration Ready
```typescript
// Cấu trúc sẵn sàng cho API
const fetchProducts = async (filters: ProductFilters) => {
  const response = await fetch('/api/products', {
    method: 'POST',
    body: JSON.stringify(filters)
  })
  return response.json()
}
```

### Planned Features
- [ ] **User Authentication**: Login/Register system
- [ ] **Shopping Cart**: Full cart functionality
- [ ] **Payment Integration**: Checkout process
- [ ] **Product Reviews**: User review system
- [ ] **Admin Dashboard**: Product management
- [ ] **Real-time Chat**: Customer support
- [ ] **PWA Features**: Offline support
- [ ] **Analytics**: User behavior tracking

## 🧪 Testing Strategy

### Unit Testing
- **Component Testing**: React Testing Library
- **Hook Testing**: Custom hooks testing
- **Utility Testing**: Pure function testing

### Integration Testing
- **User Flows**: E2E testing với Playwright
- **API Integration**: Mock API testing
- **Cross-browser**: Browser compatibility

### Performance Testing
- **Lighthouse**: Performance metrics
- **Bundle Analysis**: Code splitting effectiveness
- **Load Testing**: Stress testing

## 📊 Code Quality

### ESLint Rules
- **React Hooks**: Proper hooks usage
- **TypeScript**: Strict type checking
- **Accessibility**: a11y rules
- **Performance**: Performance best practices

### Code Standards
- **Naming Convention**: camelCase, PascalCase
- **File Structure**: Consistent organization
- **Import Order**: Organized imports
- **Comment Style**: JSDoc for functions

## 🚀 Deployment

### Build Process
```bash
# Development
npm run dev

# Production build
npm run build

# Start production server
npm start

# Type checking
npm run type-check

# Linting
npm run lint
```

### Environment Variables
```env
# API Configuration
NEXT_PUBLIC_API_URL=https://api.sunfil.vn
NEXT_PUBLIC_APP_ENV=production

# Analytics
NEXT_PUBLIC_GA_ID=GA-XXXXXXXXX
```

## 👨‍💻 Developer Experience

### Hot Reload
- **Fast Refresh**: Instant component updates
- **CSS Hot Reload**: Style changes without refresh
- **TypeScript**: Real-time type checking

### Development Tools
- **VS Code Extensions**: ESLint, Prettier, TypeScript
- **Browser DevTools**: React DevTools, Redux DevTools
- **Performance**: React Profiler, Lighthouse

## 📈 Metrics & Analytics

### Performance Metrics
- **First Contentful Paint**: < 1.5s
- **Largest Contentful Paint**: < 2.5s
- **Cumulative Layout Shift**: < 0.1
- **First Input Delay**: < 100ms

### Business Metrics
- **Conversion Rate**: Product view to cart
- **User Engagement**: Time on page, bounce rate
- **Search Success**: Search to purchase funnel

## 🤝 Contributing

### Code Review Process
1. **Feature Branch**: Create từ main branch
2. **Pull Request**: Detailed description
3. **Code Review**: Peer review required
4. **Testing**: All tests must pass
5. **Merge**: Squash and merge

### Coding Guidelines
- **Component Size**: < 200 lines
- **Function Complexity**: < 10 cyclomatic complexity
- **Test Coverage**: > 80%
- **Documentation**: JSDoc for public APIs

## 📞 Contact & Support

### Developer Information
- **Name**: [Your Name]
- **Email**: [your.email@example.com]
- **LinkedIn**: [Your LinkedIn Profile]
- **GitHub**: [Your GitHub Profile]

### Project Repository
- **GitHub**: [Repository URL]
- **Demo**: [Live Demo URL]
- **Documentation**: [Docs URL]

---

## 🎯 Kết luận

Dự án SUNFIL E-commerce thể hiện khả năng:

1. **Technical Skills**: Next.js, TypeScript, Modern React patterns
2. **Design Implementation**: Pixel-perfect UI từ Figma design
3. **Code Architecture**: Clean, maintainable, scalable code
4. **UX Thinking**: User-centered design approach
5. **Performance**: Optimized for speed và accessibility
6. **Future-ready**: Extensible architecture cho growth

Đây là một showcase hoàn chỉnh về khả năng frontend development với focus vào quality, performance và user experience.

**"Code không chỉ để chạy, mà còn để đọc, maintain và scale."**
