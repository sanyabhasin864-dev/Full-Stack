
# Full-import { useState, useContext, createContext } from "react";

// ─── CONTEXT ───────────────────────────────────────────────────────────────
const AppContext = createContext();
const useApp = () => useContext(AppContext);

// ─── MOCK DATA ──────────────────────────────────────────────────────────────
const MOVIES = [
  { id: 1, title: "Stellar Odyssey", genre: "Sci-Fi", rating: 8.4, duration: "2h 28m", language: "English", releaseDate: "2025-05-15", poster: "🚀", description: "A breathtaking journey through the cosmos as humanity makes its first contact with an advanced alien civilization. Stunning visuals and an emotionally charged story.", cast: ["Ryan Mercer", "Priya Nair", "James Holloway"], director: "Sofia Reyes", status: "Now Showing" },
  { id: 2, title: "Echoes of the Past", genre: "Thriller", rating: 7.9, duration: "2h 05m", language: "English", releaseDate: "2025-06-01", poster: "🔍", description: "A detective unravels a decades-old conspiracy that threatens to destroy the most powerful institutions of modern society.", cast: ["Amara Osei", "David Kowalski", "Leila Hassan"], director: "Marcus Webb", status: "Now Showing" },
  { id: 3, title: "Monsoon Wedding 2", genre: "Drama", rating: 8.1, duration: "2h 15m", language: "Hindi", releaseDate: "2025-05-20", poster: "💐", description: "A heartwarming sequel following the next generation as they navigate love, family expectations, and cultural traditions in modern India.", cast: ["Kavya Reddy", "Arjun Malhotra", "Sunita Bose"], director: "Mira Nair", status: "Now Showing" },
  { id: 4, title: "Iron Citadel", genre: "Action", rating: 7.6, duration: "2h 32m", language: "English", releaseDate: "2025-06-10", poster: "⚔️", description: "An elite mercenary team must infiltrate the world's most fortified underground bunker before a global catastrophe unfolds.", cast: ["Blake Torres", "Yuki Tanaka", "Femi Adeyemi"], director: "Chris Banks", status: "Now Showing" },
  { id: 5, title: "The Quiet Mountain", genre: "Drama", rating: 8.7, duration: "1h 58m", language: "French", releaseDate: "2025-04-25", poster: "🏔️", description: "An introspective tale of a renowned painter who retreats to the Alps after losing her sight, rediscovering her art through touch and memory.", cast: ["Isabelle Moreau", "Claude Petit", "Elise Renard"], director: "Luc Blanchard", status: "Now Showing" },
  { id: 6, title: "Neon Dragons", genre: "Animation", rating: 8.0, duration: "1h 45m", language: "English", releaseDate: "2025-06-15", poster: "🐉", description: "A visually dazzling animated epic set in a cyberpunk city where ancient dragon spirits awaken to battle corporate oppression.", cast: ["Voiced by: Sam Park", "Nina Chu", "Leo Fox"], director: "Studio Kinetic", status: "Coming Soon" },
  { id: 7, title: "Rajkumar Returns", genre: "Bollywood", rating: 7.5, duration: "2h 45m", language: "Hindi", releaseDate: "2025-07-04", poster: "👑", description: "The beloved Rajkumar franchise returns with a high-octane action-drama about a prince reclaiming his kingdom.", cast: ["Vikram Sharma", "Deepika Roy", "Ranjit Kumar"], director: "Sanjay Leela", status: "Coming Soon" },
  { id: 8, title: "Deep Blue Silence", genre: "Horror", rating: 7.3, duration: "1h 52m", language: "English", releaseDate: "2025-06-20", poster: "🌊", description: "A research submarine crew discovers something ancient and terrifying lurking in the deepest ocean trench on Earth.", cast: ["Elena Cross", "Mark Ashford", "Soo-Jin Park"], director: "Dean Holt", status: "Coming Soon" },
];

const CITIES = ["Mumbai", "Delhi", "Bengaluru", "Chennai", "Hyderabad", "Kolkata", "Pune", "Ahmedabad"];

const THEATRES = {
  "Mumbai": [
    { id: 1, name: "PVR Cinemas — Juhu", address: "Juhu Beach Road, Juhu", amenities: ["Dolby Atmos", "4K Screen", "Recliner Seats"], rating: 4.5 },
    { id: 2, name: "INOX — Lower Parel", address: "Phoenix Mills, Lower Parel", amenities: ["IMAX", "Dolby Atmos"], rating: 4.3 },
    { id: 3, name: "Cinepolis — Andheri", address: "Infinity Mall, Andheri", amenities: ["4DX", "Recliner Seats"], rating: 4.1 },
  ],
  "Delhi": [
    { id: 4, name: "PVR — Select Citywalk", address: "Saket, South Delhi", amenities: ["IMAX", "Dolby Atmos"], rating: 4.6 },
    { id: 5, name: "INOX — CP", address: "Connaught Place, Central Delhi", amenities: ["4K Screen"], rating: 4.2 },
  ],
  "Bengaluru": [
    { id: 6, name: "PVR — Orion Mall", address: "Rajajinagar, Bengaluru", amenities: ["Dolby Atmos", "IMAX"], rating: 4.4 },
  ],
};

const SCREENS = [
  { id: 1, name: "Audi 1 — IMAX", type: "IMAX", capacity: 280, features: ["Laser Projection", "Dolby Atmos"] },
  { id: 2, name: "Audi 2 — Premium", type: "Premium", capacity: 180, features: ["Recliner Seats", "4K"] },
  { id: 3, name: "Audi 3 — Standard", type: "Standard", capacity: 240, features: ["Digital Projection"] },
];

const SHOWTIMES = ["10:00 AM", "12:30 PM", "3:15 PM", "6:00 PM", "9:30 PM", "11:55 PM"];

const BOOKING_HISTORY = [
  { id: "BK001", movie: "Stellar Odyssey", theatre: "PVR Cinemas — Juhu", date: "2025-05-28", time: "6:00 PM", seats: ["F5", "F6"], total: 580, status: "Confirmed" },
  { id: "BK002", movie: "The Quiet Mountain", theatre: "INOX — Lower Parel", date: "2025-05-15", time: "3:15 PM", seats: ["C3"], total: 260, status: "Confirmed" },
  { id: "BK003", movie: "Iron Citadel", theatre: "Cinepolis — Andheri", date: "2025-04-20", time: "9:30 PM", seats: ["A1", "A2", "A3"], total: 720, status: "Cancelled" },
];

const ADMIN_USERS = [
  { id: 1, name: "Ananya Sharma", email: "ananya@email.com", role: "Customer", joined: "2025-01-10", bookings: 12, status: "Active" },
  { id: 2, name: "Rohan Verma", email: "rohan@theatres.com", role: "Theatre Owner", joined: "2025-02-01", bookings: 0, status: "Active" },
  { id: 3, name: "Meera Pillai", email: "meera@email.com", role: "Customer", joined: "2025-03-15", bookings: 5, status: "Active" },
  { id: 4, name: "Kabir Singh", email: "kabir@cinemas.co", role: "Theatre Owner", joined: "2025-04-05", bookings: 0, status: "Pending" },
  { id: 5, name: "Divya Nair", email: "divya@email.com", role: "Customer", joined: "2025-05-01", bookings: 3, status: "Active" },
];

const ADMIN_THEATRES = [
  { id: 1, name: "PVR Cinemas — Juhu", owner: "Rohan Verma", city: "Mumbai", screens: 5, status: "Approved" },
  { id: 2, name: "SilverScreen — Whitefield", owner: "Kabir Singh", city: "Bengaluru", screens: 3, status: "Pending" },
  { id: 3, name: "StarCinema — Salt Lake", owner: "Priya Das", city: "Kolkata", screens: 4, status: "Approved" },
  { id: 4, name: "Luxe Frames — Jubilee Hills", owner: "Sanjay Reddy", city: "Hyderabad", screens: 6, status: "Pending" },
];

const OWNER_SHOWS = [
  { id: 1, movie: "Stellar Odyssey", screen: "Audi 1 — IMAX", date: "2025-06-10", times: ["10:00 AM", "2:30 PM", "7:00 PM"], bookings: 210 },
  { id: 2, movie: "Echoes of the Past", screen: "Audi 2 — Premium", date: "2025-06-10", times: ["12:00 PM", "4:00 PM", "9:00 PM"], bookings: 145 },
  { id: 3, movie: "Iron Citadel", screen: "Audi 3 — Standard", date: "2025-06-10", times: ["11:00 AM", "3:30 PM", "8:00 PM"], bookings: 98 },
];

// ─── STYLES ─────────────────────────────────────────────────────────────────
const S = {
  app: { fontFamily: "system-ui, -apple-system, sans-serif", minHeight: "100vh", background: "#0a0a0f", color: "#e8e8f0" },
  nav: { background: "#12121a", borderBottom: "1px solid #2a2a3a", padding: "0 24px", display: "flex", alignItems: "center", justifyContent: "space-between", height: 60, position: "sticky", top: 0, zIndex: 100 },
  logo: { fontSize: 22, fontWeight: 700, color: "#e85d26", letterSpacing: "-0.5px", cursor: "pointer" },
  navLinks: { display: "flex", gap: 4, alignItems: "center" },
  navBtn: (active) => ({ background: active ? "#1e1e2e" : "transparent", border: "none", color: active ? "#e85d26" : "#9090a8", padding: "6px 14px", borderRadius: 8, cursor: "pointer", fontSize: 14, fontWeight: active ? 500 : 400 }),
  sidebar: { width: 220, background: "#12121a", borderRight: "1px solid #2a2a3a", minHeight: "calc(100vh - 60px)", padding: "20px 0", flexShrink: 0 },
  sideItem: (active) => ({ display: "flex", alignItems: "center", gap: 10, padding: "10px 20px", cursor: "pointer", color: active ? "#e85d26" : "#9090a8", background: active ? "#1e1e2e" : "transparent", borderLeft: active ? "3px solid #e85d26" : "3px solid transparent", fontSize: 14, fontWeight: active ? 500 : 400 }),
  content: { flex: 1, padding: "28px 32px", overflowY: "auto" },
  layout: { display: "flex", minHeight: "calc(100vh - 60px)" },
  h1: { fontSize: 26, fontWeight: 700, color: "#f0f0fa", margin: "0 0 6px" },
  h2: { fontSize: 20, fontWeight: 600, color: "#f0f0fa", margin: "0 0 16px" },
  h3: { fontSize: 16, fontWeight: 600, color: "#f0f0fa", margin: "0 0 8px" },
  card: { background: "#1a1a26", border: "1px solid #2a2a3a", borderRadius: 12, padding: "20px 24px" },
  movieCard: { background: "#1a1a26", border: "1px solid #2a2a3a", borderRadius: 12, overflow: "hidden", cursor: "pointer", transition: "border-color 0.2s" },
  btn: (variant = "primary") => ({
    background: variant === "primary" ? "#e85d26" : variant === "secondary" ? "transparent" : variant === "danger" ? "#7a1a1a" : "#1e1e2e",
    border: variant === "secondary" ? "1px solid #3a3a4a" : "none",
    color: variant === "muted" ? "#9090a8" : "#fff",
    padding: "9px 20px", borderRadius: 8, cursor: "pointer", fontSize: 14, fontWeight: 500
  }),
  input: { background: "#1a1a26", border: "1px solid #2a2a3a", color: "#e8e8f0", padding: "10px 14px", borderRadius: 8, fontSize: 14, width: "100%", boxSizing: "border-box" },
  badge: (color) => ({
    background: color === "green" ? "#1a3a1a" : color === "orange" ? "#3a2010" : color === "red" ? "#3a1010" : "#1e1e2e",
    color: color === "green" ? "#5dcc7a" : color === "orange" ? "#e89444" : color === "red" ? "#e85555" : "#9090a8",
    padding: "3px 10px", borderRadius: 20, fontSize: 12, fontWeight: 500, display: "inline-block"
  }),
  statsCard: { background: "#1a1a26", border: "1px solid #2a2a3a", borderRadius: 12, padding: "20px 24px" },
  seatBtn: (status) => ({
    width: 36, height: 36, borderRadius: 6, border: "none", cursor: status === "booked" ? "not-allowed" : "pointer",
    background: status === "selected" ? "#e85d26" : status === "booked" ? "#2a2a3a" : "#1e1e2e",
    color: status === "booked" ? "#3a3a4a" : "#e8e8f0", fontSize: 11, fontWeight: 500
  }),
  tag: { background: "#1e1e2e", color: "#9090a8", padding: "4px 10px", borderRadius: 20, fontSize: 12 },
  divider: { border: "none", borderTop: "1px solid #2a2a3a", margin: "20px 0" },
  subtext: { color: "#9090a8", fontSize: 14 },
};

// ─── SHARED COMPONENTS ──────────────────────────────────────────────────────
function Navbar() {
  const { user, setScreen, screen } = useApp();
  const isAdmin = user?.role === "admin";
  const isOwner = user?.role === "owner";

  return (
    <nav style={S.nav}>
      <div style={S.logo} onClick={() => setScreen(user ? (isAdmin ? "adminDash" : isOwner ? "ownerDash" : "home") : "login")}>
        🎬 CineVerse
      </div>
      {user && (
        <div style={S.navLinks}>
          {!isAdmin && !isOwner && (
            <>
              <button style={S.navBtn(screen === "home")} onClick={() => setScreen("home")}>Movies</button>
              <button style={S.navBtn(screen === "history")} onClick={() => setScreen("history")}>My Bookings</button>
            </>
          )}
          <button style={S.navBtn(screen === "profile")} onClick={() => setScreen("profile")}>👤 {user.name.split(" ")[0]}</button>
          <button style={{ ...S.btn("secondary"), marginLeft: 8 }} onClick={() => setScreen("login")}>Sign Out</button>
        </div>
      )}
    </nav>
  );
}

function Sidebar({ items, activeItem, onSelect }) {
  return (
    <div style={S.sidebar}>
      {items.map(item => (
        <div key={item.key} style={S.sideItem(activeItem === item.key)} onClick={() => onSelect(item.key)}>
          <span>{item.icon}</span><span>{item.label}</span>
        </div>
      ))}
    </div>
  );
}

function Modal({ title, children, onClose }) {
  return (
    <div style={{ position: "fixed", inset: 0, background: "rgba(0,0,0,0.7)", zIndex: 200, display: "flex", alignItems: "center", justifyContent: "center" }}>
      <div style={{ ...S.card, width: 440, maxWidth: "90vw" }}>
        <div style={{ display: "flex", justifyContent: "space-between", alignItems: "center", marginBottom: 16 }}>
          <h3 style={{ ...S.h3, margin: 0 }}>{title}</h3>
          <button onClick={onClose} style={{ background: "none", border: "none", color: "#9090a8", fontSize: 20, cursor: "pointer" }}>✕</button>
        </div>
        {children}
      </div>
    </div>
  );
}

function StarRating({ rating }) {
  return <span style={{ color: "#e8a020" }}>{"★".repeat(Math.round(rating / 2))}{"☆".repeat(5 - Math.round(rating / 2))} <span style={{ color: "#9090a8", fontSize: 13 }}>{rating}</span></span>;
}

// ─── AUTH SCREENS ────────────────────────────────────────────────────────────
function LoginPage() {
  const { setUser, setScreen } = useApp();
  const [email, setEmail] = useState("");
  const [password, setPassword] = useState("");
  const [role, setRole] = useState("customer");
  const [error, setError] = useState("");

  const handleLogin = () => {
    if (!email || !password) { setError("Please fill in all fields."); return; }
    const userMap = {
      customer: { name: "Ananya Sharma", email, role: "customer", avatar: "AS", city: "Mumbai", phone: "+91 98765 43210" },
      owner: { name: "Rohan Verma", email, role: "owner", avatar: "RV", theatre: "PVR Cinemas — Juhu" },
      admin: { name: "Admin User", email, role: "admin", avatar: "AU" },
    };
    setUser(userMap[role]);
    setScreen(role === "admin" ? "adminDash" : role === "owner" ? "ownerDash" : "home");
  };

  return (
    <div style={{ minHeight: "100vh", background: "#0a0a0f", display: "flex", alignItems: "center", justifyContent: "center", padding: 20 }}>
      <div style={{ width: 400 }}>
        <div style={{ textAlign: "center", marginBottom: 36 }}>
          <div style={{ fontSize: 48, marginBottom: 8 }}>🎬</div>
          <h1 style={{ ...S.h1, textAlign: "center" }}>CineVerse</h1>
          <p style={S.subtext}>Your world of cinema</p>
        </div>
        <div style={S.card}>
          <h2 style={{ ...S.h2, marginBottom: 20 }}>Sign In</h2>
          {error && <div style={{ background: "#3a1010", border: "1px solid #7a2020", color: "#e85555", padding: "10px 14px", borderRadius: 8, marginBottom: 16, fontSize: 14 }}>{error}</div>}
          <div style={{ marginBottom: 16 }}>
            <label style={{ display: "block", fontSize: 13, color: "#9090a8", marginBottom: 6 }}>Email</label>
            <input style={S.input} type="email" placeholder="you@example.com" value={email} onChange={e => setEmail(e.target.value)} />
          </div>
          <div style={{ marginBottom: 16 }}>
            <label style={{ display: "block", fontSize: 13, color: "#9090a8", marginBottom: 6 }}>Password</label>
            <input style={S.input} type="password" placeholder="••••••••" value={password} onChange={e => setPassword(e.target.value)} />
          </div>
          <div style={{ marginBottom: 24 }}>
            <label style={{ display: "block", fontSize: 13, color: "#9090a8", marginBottom: 6 }}>Sign in as</label>
            <div style={{ display: "flex", gap: 8 }}>
              {["customer", "owner", "admin"].map(r => (
                <button key={r} onClick={() => setRole(r)} style={{ ...S.btn(role === r ? "primary" : "secondary"), flex: 1, textTransform: "capitalize" }}>{r}</button>
              ))}
            </div>
          </div>
          <button onClick={handleLogin} style={{ ...S.btn("primary"), width: "100%", padding: "12px 20px", fontSize: 15 }}>Sign In</button>
          <p style={{ textAlign: "center", marginTop: 16, fontSize: 14, color: "#9090a8" }}>
            No account? <span style={{ color: "#e85d26", cursor: "pointer" }} onClick={() => setScreen("signup")}>Create one</span>
          </p>
        </div>
      </div>
    </div>
  );
}

function SignupPage() {
  const { setScreen } = useApp();
  const [form, setForm] = useState({ name: "", email: "", phone: "", password: "", confirm: "" });
  const update = k => e => setForm(f => ({ ...f, [k]: e.target.value }));

  return (
    <div style={{ minHeight: "100vh", background: "#0a0a0f", display: "flex", alignItems: "center", justifyContent: "center", padding: 20 }}>
      <div style={{ width: 440 }}>
        <div style={{ textAlign: "center", marginBottom: 32 }}>
          <div style={{ fontSize: 48, marginBottom: 8 }}>🎬</div>
          <h1 style={{ ...S.h1, textAlign: "center" }}>Create Account</h1>
        </div>
        <div style={S.card}>
          {[["Full Name", "name", "text", "Jane Doe"], ["Email Address", "email", "email", "you@example.com"], ["Phone Number", "phone", "tel", "+91 98765 43210"], ["Password", "password", "password", "••••••••"], ["Confirm Password", "confirm", "password", "••••••••"]].map(([label, key, type, ph]) => (
            <div key={key} style={{ marginBottom: 16 }}>
              <label style={{ display: "block", fontSize: 13, color: "#9090a8", marginBottom: 6 }}>{label}</label>
              <input style={S.input} type={type} placeholder={ph} value={form[key]} onChange={update(key)} />
            </div>
          ))}
          <div style={{ marginBottom: 20 }}>
            <label style={{ display: "block", fontSize: 13, color: "#9090a8", marginBottom: 6 }}>I am registering as</label>
            <select style={{ ...S.input }}>
              <option>Customer</option>
              <option>Theatre Owner</option>
            </select>
          </div>
          <button onClick={() => setScreen("login")} style={{ ...S.btn("primary"), width: "100%", padding: "12px 20px", fontSize: 15 }}>Create Account</button>
          <p style={{ textAlign: "center", marginTop: 16, fontSize: 14, color: "#9090a8" }}>
            Already have an account? <span style={{ color: "#e85d26", cursor: "pointer" }} onClick={() => setScreen("login")}>Sign in</span>
          </p>
        </div>
      </div>
    </div>
  );
}

// ─── CUSTOMER SCREENS ────────────────────────────────────────────────────────
function HomePage() {
  const { setScreen, setBooking, user } = useApp();
  const [search, setSearch] = useState("");
  const [filterGenre, setFilterGenre] = useState("All");
  const genres = ["All", ...new Set(MOVIES.map(m => m.genre))];
  const filtered = MOVIES.filter(m =>
    (filterGenre === "All" || m.genre === filterGenre) &&
    m.title.toLowerCase().includes(search.toLowerCase())
  );
  const nowShowing = filtered.filter(m => m.status === "Now Showing");
  const comingSoon = filtered.filter(m => m.status === "Coming Soon");

  return (
    <div>
      <div style={{ background: "linear-gradient(180deg,#1a0a0a 0%,#0a0a0f 100%)", padding: "32px 0 24px", marginBottom: 28 }}>
        <h1 style={{ ...S.h1, marginBottom: 4 }}>Welcome back, {user?.name.split(" ")[0]} 👋</h1>
        <p style={S.subtext}>Discover great films playing near you</p>
        <div style={{ display: "flex", gap: 12, marginTop: 20, flexWrap: "wrap" }}>
          <input style={{ ...S.input, maxWidth: 340 }} placeholder="Search movies..." value={search} onChange={e => setSearch(e.target.value)} />
          <div style={{ display: "flex", gap: 8, flexWrap: "wrap" }}>
            {genres.map(g => <button key={g} onClick={() => setFilterGenre(g)} style={{ ...S.btn(filterGenre === g ? "primary" : "secondary") }}>{g}</button>)}
          </div>
        </div>
      </div>

      {nowShowing.length > 0 && (
        <>
          <h2 style={S.h2}>Now Showing</h2>
          <div style={{ display: "grid", gridTemplateColumns: "repeat(auto-fill, minmax(200px, 1fr))", gap: 16, marginBottom: 36 }}>
            {nowShowing.map(movie => (
              <MovieCard key={movie.id} movie={movie} onClick={() => { setBooking({ movie }); setScreen("movieDetail"); }} />
            ))}
          </div>
        </>
      )}
      {comingSoon.length > 0 && (
        <>
          <h2 style={S.h2}>Coming Soon</h2>
          <div style={{ display: "grid", gridTemplateColumns: "repeat(auto-fill, minmax(200px, 1fr))", gap: 16 }}>
            {comingSoon.map(movie => (
              <MovieCard key={movie.id} movie={movie} comingSoon onClick={() => { setBooking({ movie }); setScreen("movieDetail"); }} />
            ))}
          </div>
        </>
      )}
    </div>
  );
}

function MovieCard({ movie, onClick, comingSoon }) {
  const [hover, setHover] = useState(false);
  return (
    <div style={{ ...S.movieCard, borderColor: hover ? "#e85d26" : "#2a2a3a" }}
      onClick={!comingSoon ? onClick : undefined}
      onMouseEnter={() => setHover(true)} onMouseLeave={() => setHover(false)}>
      <div style={{ height: 160, background: "#12121a", display: "flex", alignItems: "center", justifyContent: "center", fontSize: 60 }}>{movie.poster}</div>
      <div style={{ padding: "14px 16px" }}>
        <div style={{ fontSize: 15, fontWeight: 600, color: "#f0f0fa", marginBottom: 4, whiteSpace: "nowrap", overflow: "hidden", textOverflow: "ellipsis" }}>{movie.title}</div>
        <div style={{ display: "flex", justifyContent: "space-between", alignItems: "center", marginBottom: 8 }}>
          <span style={S.tag}>{movie.genre}</span>
          <span style={{ color: "#e8a020", fontSize: 13 }}>★ {movie.rating}</span>
        </div>
        <div style={{ fontSize: 12, color: "#9090a8", marginBottom: 10 }}>{movie.language} · {movie.duration}</div>
        {comingSoon
          ? <div style={{ ...S.badge("orange"), textAlign: "center", width: "100%", boxSizing: "border-box" }}>Coming Soon</div>
          : <button style={{ ...S.btn("primary"), width: "100%", fontSize: 13 }} onClick={onClick}>Book Now</button>
        }
      </div>
    </div>
  );
}

function MovieDetailPage() {
  const { booking, setBooking, setScreen } = useApp();
  const movie = booking?.movie;
  if (!movie) return null;

  return (
    <div>
      <button style={{ ...S.btn("secondary"), marginBottom: 20 }} onClick={() => setScreen("home")}>← Back</button>
      <div style={{ display: "grid", gridTemplateColumns: "240px 1fr", gap: 32, marginBottom: 28 }}>
        <div style={{ background: "#12121a", borderRadius: 12, height: 340, display: "flex", alignItems: "center", justifyContent: "center", fontSize: 90 }}>{movie.poster}</div>
        <div>
          <div style={{ display: "flex", gap: 10, marginBottom: 10, flexWrap: "wrap" }}>
            <span style={S.tag}>{movie.genre}</span>
            <span style={S.tag}>{movie.language}</span>
            <span style={S.tag}>{movie.duration}</span>
            <span style={S.badge(movie.status === "Now Showing" ? "green" : "orange")}>{movie.status}</span>
          </div>
          <h1 style={{ ...S.h1, fontSize: 32 }}>{movie.title}</h1>
          <StarRating rating={movie.rating} />
          <p style={{ color: "#c0c0d8", lineHeight: 1.7, marginTop: 16, marginBottom: 20 }}>{movie.description}</p>
          <div style={{ display: "grid", gridTemplateColumns: "1fr 1fr", gap: 12, marginBottom: 24 }}>
            <div style={S.statsCard}><div style={S.subtext}>Director</div><div style={{ fontWeight: 500, marginTop: 4 }}>{movie.director}</div></div>
            <div style={S.statsCard}><div style={S.subtext}>Release Date</div><div style={{ fontWeight: 500, marginTop: 4 }}>{movie.releaseDate}</div></div>
          </div>
          <div style={S.statsCard}><div style={{ ...S.subtext, marginBottom: 6 }}>Cast</div><div style={{ fontWeight: 500 }}>{movie.cast.join(", ")}</div></div>
          {movie.status === "Now Showing" && (
            <button style={{ ...S.btn("primary"), marginTop: 20, padding: "12px 32px", fontSize: 15 }}
              onClick={() => setScreen("locationSelect")}>Book Tickets →</button>
          )}
        </div>
      </div>
    </div>
  );
}

function LocationSelectPage() {
  const { setBooking, setScreen, booking } = useApp();
  return (
    <div>
      <button style={{ ...S.btn("secondary"), marginBottom: 20 }} onClick={() => setScreen("movieDetail")}>← Back</button>
      <h1 style={S.h1}>Select Your City</h1>
      <p style={{ ...S.subtext, marginBottom: 28 }}>Booking for: <strong style={{ color: "#e8e8f0" }}>{booking?.movie?.title}</strong></p>
      <div style={{ display: "grid", gridTemplateColumns: "repeat(auto-fill, minmax(160px, 1fr))", gap: 12 }}>
        {CITIES.map(city => (
          <button key={city} style={{ ...S.card, cursor: "pointer", border: "1px solid #2a2a3a", textAlign: "center", fontSize: 16, fontWeight: 500, padding: "24px 16px" }}
            onClick={() => { setBooking(b => ({ ...b, city })); setScreen("theatreSelect"); }}>
            🏙️<br /><span style={{ fontSize: 14 }}>{city}</span>
          </button>
        ))}
      </div>
    </div>
  );
}

function TheatreSelectPage() {
  const { booking, setBooking, setScreen } = useApp();
  const theatres = THEATRES[booking?.city] || THEATRES["Mumbai"];

  return (
    <div>
      <button style={{ ...S.btn("secondary"), marginBottom: 20 }} onClick={() => setScreen("locationSelect")}>← Back</button>
      <h1 style={S.h1}>Select Theatre</h1>
      <p style={{ ...S.subtext, marginBottom: 28 }}>{booking?.city} · {booking?.movie?.title}</p>
      <div style={{ display: "flex", flexDirection: "column", gap: 14 }}>
        {theatres.map(t => (
          <div key={t.id} style={{ ...S.card, cursor: "pointer", display: "flex", justifyContent: "space-between", alignItems: "center" }}
            onClick={() => { setBooking(b => ({ ...b, theatre: t })); setScreen("screenSelect"); }}>
            <div>
              <div style={{ fontWeight: 600, fontSize: 16, marginBottom: 4 }}>{t.name}</div>
              <div style={{ ...S.subtext, marginBottom: 8 }}>📍 {t.address}</div>
              <div style={{ display: "flex", gap: 8, flexWrap: "wrap" }}>{t.amenities.map(a => <span key={a} style={S.tag}>{a}</span>)}</div>
            </div>
            <div style={{ textAlign: "right" }}>
              <div style={{ color: "#e8a020", marginBottom: 8 }}>★ {t.rating}</div>
              <button style={S.btn("primary")}>Select →</button>
            </div>
          </div>
        ))}
      </div>
    </div>
  );
}

function ScreenSelectPage() {
  const { booking, setBooking, setScreen } = useApp();
  return (
    <div>
      <button style={{ ...S.btn("secondary"), marginBottom: 20 }} onClick={() => setScreen("theatreSelect")}>← Back</button>
      <h1 style={S.h1}>Select Auditorium</h1>
      <p style={{ ...S.subtext, marginBottom: 28 }}>{booking?.theatre?.name}</p>
      <div style={{ display: "grid", gridTemplateColumns: "repeat(auto-fill, minmax(280px, 1fr))", gap: 14 }}>
        {SCREENS.map(s => (
          <div key={s.id} style={{ ...S.card, cursor: "pointer", borderColor: s.type === "IMAX" ? "#e85d26" : "#2a2a3a" }}
            onClick={() => { setBooking(b => ({ ...b, screen: s })); setScreen("showtimeSelect"); }}>
            <div style={{ display: "flex", justifyContent: "space-between", alignItems: "flex-start", marginBottom: 10 }}>
              <h3 style={{ ...S.h3, margin: 0 }}>{s.name}</h3>
              {s.type === "IMAX" && <span style={S.badge("orange")}>Premium</span>}
            </div>
            <div style={{ ...S.subtext, marginBottom: 10 }}>Capacity: {s.capacity} seats</div>
            <div style={{ display: "flex", gap: 8, flexWrap: "wrap" }}>{s.features.map(f => <span key={f} style={S.tag}>{f}</span>)}</div>
            <button style={{ ...S.btn("primary"), marginTop: 14, width: "100%" }}>Choose Showtime</button>
          </div>
        ))}
      </div>
    </div>
  );
}

function ShowtimeSelectPage() {
  const { booking, setBooking, setScreen } = useApp();
  const [selected, setSelected] = useState(null);
  const [date, setDate] = useState("2025-06-10");

  return (
    <div>
      <button style={{ ...S.btn("secondary"), marginBottom: 20 }} onClick={() => setScreen("screenSelect")}>← Back</button>
      <h1 style={S.h1}>Select Showtime</h1>
      <p style={{ ...S.subtext, marginBottom: 24 }}>{booking?.screen?.name} · {booking?.theatre?.name}</p>
      <div style={{ marginBottom: 24 }}>
        <label style={{ display: "block", fontSize: 13, color: "#9090a8", marginBottom: 6 }}>Date</label>
        <input type="date" style={{ ...S.input, maxWidth: 220 }} value={date} onChange={e => setDate(e.target.value)} min="2025-06-10" max="2025-06-20" />
      </div>
      <div style={{ display: "grid", gridTemplateColumns: "repeat(auto-fill, minmax(140px, 1fr))", gap: 12, marginBottom: 28 }}>
        {SHOWTIMES.map(t => (
          <button key={t} onClick={() => setSelected(t)}
            style={{ ...S.card, cursor: "pointer", textAlign: "center", padding: "16px 12px", borderColor: selected === t ? "#e85d26" : "#2a2a3a", color: selected === t ? "#e85d26" : "#e8e8f0", fontWeight: selected === t ? 600 : 400 }}>
            🕐 {t}
            <div style={{ ...S.subtext, fontSize: 12, marginTop: 6 }}>Avail.</div>
          </button>
        ))}
      </div>
      <button disabled={!selected} onClick={() => { setBooking(b => ({ ...b, showtime: selected, date })); setScreen("seatSelect"); }}
        style={{ ...S.btn(selected ? "primary" : "muted"), padding: "12px 32px", fontSize: 15, cursor: selected ? "pointer" : "not-allowed" }}>
        Proceed to Seat Selection →
      </button>
    </div>
  );
}

function SeatSelectPage() {
  const { booking, setBooking, setScreen } = useApp();
  const [selectedSeats, setSelectedSeats] = useState([]);
  const rows = ["A", "B", "C", "D", "E", "F", "G", "H"];
  const cols = Array.from({ length: 12 }, (_, i) => i + 1);
  const bookedSeats = ["A3", "A4", "B7", "C2", "C3", "C4", "D9", "D10", "E5", "F1", "F2", "G8", "H11", "H12"];
  const PRICE = booking?.screen?.type === "IMAX" ? 320 : booking?.screen?.type === "Premium" ? 280 : 200;

  const toggle = (seat) => {
    if (bookedSeats.includes(seat)) return;
    setSelectedSeats(s => s.includes(seat) ? s.filter(x => x !== seat) : [...s, seat]);
  };

  return (
    <div>
      <button style={{ ...S.btn("secondary"), marginBottom: 20 }} onClick={() => setScreen("showtimeSelect")}>← Back</button>
      <h1 style={S.h1}>Select Your Seats</h1>
      <p style={{ ...S.subtext, marginBottom: 20 }}>{booking?.movie?.title} · {booking?.showtime} · {booking?.date}</p>
      <div style={{ background: "#1a1a26", border: "1px solid #2a2a3a", borderRadius: 12, padding: 24, marginBottom: 20, overflowX: "auto" }}>
        <div style={{ textAlign: "center", background: "#e85d26", borderRadius: "40px 40px 4px 4px", padding: "8px 0", marginBottom: 24, maxWidth: 460, margin: "0 auto 24px" }}>
          <span style={{ fontSize: 13, fontWeight: 500 }}>SCREEN</span>
        </div>
        {rows.map(row => (
          <div key={row} style={{ display: "flex", alignItems: "center", gap: 8, marginBottom: 8, justifyContent: "center" }}>
            <span style={{ width: 20, textAlign: "right", fontSize: 13, color: "#9090a8" }}>{row}</span>
            <div style={{ display: "flex", gap: 6 }}>
              {cols.map(col => {
                const seat = `${row}${col}`;
                const status = bookedSeats.includes(seat) ? "booked" : selectedSeats.includes(seat) ? "selected" : "available";
                return <button key={col} style={S.seatBtn(status)} onClick={() => toggle(seat)} title={seat}>{col}</button>;
              })}
            </div>
          </div>
        ))}
        <div style={{ display: "flex", gap: 20, justifyContent: "center", marginTop: 20 }}>
          {[["#1e1e2e", "Available"], ["#e85d26", "Selected"], ["#2a2a3a", "Booked"]].map(([bg, label]) => (
            <div key={label} style={{ display: "flex", alignItems: "center", gap: 6, fontSize: 12, color: "#9090a8" }}>
              <div style={{ width: 16, height: 16, background: bg, borderRadius: 4 }} />{label}
            </div>
          ))}
        </div>
      </div>
      <div style={{ display: "flex", justifyContent: "space-between", alignItems: "center", ...S.card }}>
        <div>
          <span style={S.subtext}>Selected: </span>
          <strong>{selectedSeats.length > 0 ? selectedSeats.join(", ") : "None"}</strong>
          <span style={{ ...S.subtext, marginLeft: 16 }}>Total: </span>
          <strong style={{ color: "#e85d26" }}>₹{selectedSeats.length * PRICE}</strong>
        </div>
        <button disabled={selectedSeats.length === 0}
          onClick={() => { setBooking(b => ({ ...b, seats: selectedSeats, pricePerSeat: PRICE })); setScreen("bookingSummary"); }}
          style={{ ...S.btn(selectedSeats.length > 0 ? "primary" : "muted"), padding: "10px 24px", cursor: selectedSeats.length > 0 ? "pointer" : "not-allowed" }}>
          Continue →
        </button>
      </div>
    </div>
  );
}

function BookingSummaryPage() {
  const { booking, setScreen } = useApp();
  const [showModal, setShowModal] = useState(false);
  const total = (booking?.seats?.length || 0) * (booking?.pricePerSeat || 0);
  const convenience = Math.round(total * 0.05);

  return (
    <div style={{ maxWidth: 560 }}>
      <button style={{ ...S.btn("secondary"), marginBottom: 20 }} onClick={() => setScreen("seatSelect")}>← Back</button>
      <h1 style={S.h1}>Booking Summary</h1>
      <div style={{ ...S.card, marginBottom: 16 }}>
        <div style={{ display: "flex", gap: 16, marginBottom: 16 }}>
          <div style={{ fontSize: 48 }}>{booking?.movie?.poster}</div>
          <div>
            <div style={{ fontWeight: 600, fontSize: 18, marginBottom: 4 }}>{booking?.movie?.title}</div>
            <div style={S.subtext}>{booking?.movie?.genre} · {booking?.movie?.language}</div>
          </div>
        </div>
        <hr style={S.divider} />
        {[
          ["Theatre", booking?.theatre?.name],
          ["Screen", booking?.screen?.name],
          ["Date & Time", `${booking?.date} at ${booking?.showtime}`],
          ["Seats", booking?.seats?.join(", ")],
          ["Seat Type", booking?.screen?.type],
        ].map(([k, v]) => (
          <div key={k} style={{ display: "flex", justifyContent: "space-between", marginBottom: 10 }}>
            <span style={S.subtext}>{k}</span>
            <span style={{ fontWeight: 500 }}>{v}</span>
          </div>
        ))}
        <hr style={S.divider} />
        {[
          [`Tickets (${booking?.seats?.length} × ₹${booking?.pricePerSeat})`, `₹${total}`],
          ["Convenience Fee", `₹${convenience}`],
        ].map(([k, v]) => (
          <div key={k} style={{ display: "flex", justifyContent: "space-between", marginBottom: 10 }}>
            <span style={S.subtext}>{k}</span><span>{v}</span>
          </div>
        ))}
        <div style={{ display: "flex", justifyContent: "space-between", fontWeight: 700, fontSize: 18, marginTop: 8 }}>
          <span>Total</span><span style={{ color: "#e85d26" }}>₹{total + convenience}</span>
        </div>
      </div>
      <div style={{ ...S.card, marginBottom: 20 }}>
        <h3 style={S.h3}>Payment Method</h3>
        {["UPI / GPay", "Credit / Debit Card", "Net Banking", "Wallets"].map((m, i) => (
          <label key={m} style={{ display: "flex", alignItems: "center", gap: 10, padding: "10px 0", borderBottom: i < 3 ? "1px solid #2a2a3a" : "none", cursor: "pointer" }}>
            <input type="radio" name="payment" defaultChecked={i === 0} style={{ accentColor: "#e85d26" }} />
            <span style={{ fontSize: 14 }}>{m}</span>
          </label>
        ))}
      </div>
      <button style={{ ...S.btn("primary"), width: "100%", padding: "14px 20px", fontSize: 16 }} onClick={() => setShowModal(true)}>
        Pay ₹{total + convenience}
      </button>
      {showModal && (
        <Modal title="Confirm Payment" onClose={() => setShowModal(false)}>
          <p style={{ ...S.subtext, marginBottom: 20 }}>You are about to pay <strong style={{ color: "#e85d26" }}>₹{total + convenience}</strong> for {booking?.seats?.length} seat(s).</p>
          <div style={{ display: "flex", gap: 12 }}>
            <button style={{ ...S.btn("secondary"), flex: 1 }} onClick={() => setShowModal(false)}>Cancel</button>
            <button style={{ ...S.btn("primary"), flex: 1 }} onClick={() => { setShowModal(false); setScreen("bookingConfirm"); }}>Confirm & Pay</button>
          </div>
        </Modal>
      )}
    </div>
  );
}

function BookingConfirmPage() {
  const { booking, setScreen } = useApp();
  const confirmId = "BK" + Math.floor(10000 + Math.random() * 90000);
  const total = (booking?.seats?.length || 0) * (booking?.pricePerSeat || 0);

  return (
    <div style={{ maxWidth: 520, margin: "0 auto", textAlign: "center" }}>
      <div style={{ fontSize: 72, marginBottom: 16 }}>✅</div>
      <h1 style={{ ...S.h1, textAlign: "center", marginBottom: 8 }}>Booking Confirmed!</h1>
      <p style={{ ...S.subtext, marginBottom: 32 }}>Your tickets have been booked successfully</p>
      <div style={{ ...S.card, textAlign: "left", marginBottom: 24 }}>
        <div style={{ background: "#0a0a0f", borderRadius: 8, padding: "12px 16px", textAlign: "center", marginBottom: 20 }}>
          <div style={{ fontSize: 12, color: "#9090a8", marginBottom: 4 }}>Booking ID</div>
          <div style={{ fontSize: 24, fontWeight: 700, color: "#e85d26", letterSpacing: 2 }}>{confirmId}</div>
        </div>
        {[
          ["Movie", booking?.movie?.title],
          ["Theatre", booking?.theatre?.name],
          ["Date & Time", `${booking?.date} at ${booking?.showtime}`],
          ["Seats", booking?.seats?.join(", ")],
          ["Amount Paid", `₹${total + Math.round(total * 0.05)}`],
        ].map(([k, v]) => (
          <div key={k} style={{ display: "flex", justifyContent: "space-between", padding: "8px 0", borderBottom: "1px solid #1e1e2e" }}>
            <span style={S.subtext}>{k}</span><span style={{ fontWeight: 500 }}>{v}</span>
          </div>
        ))}
      </div>
      <div style={{ display: "flex", gap: 12, justifyContent: "center" }}>
        <button style={S.btn("secondary")} onClick={() => setScreen("history")}>View All Bookings</button>
        <button style={S.btn("primary")} onClick={() => setScreen("home")}>Back to Movies</button>
      </div>
    </div>
  );
}

function ProfilePage() {
  const { user, setScreen } = useApp();
  const [editing, setEditing] = useState(false);
  return (
    <div style={{ maxWidth: 600 }}>
      <h1 style={S.h1}>My Profile</h1>
      <div style={{ ...S.card, marginBottom: 20 }}>
        <div style={{ display: "flex", alignItems: "center", gap: 20, marginBottom: 24 }}>
          <div style={{ width: 72, height: 72, borderRadius: "50%", background: "#e85d26", display: "flex", alignItems: "center", justifyContent: "center", fontSize: 24, fontWeight: 700 }}>{user?.avatar}</div>
          <div>
            <h2 style={{ ...S.h2, margin: 0 }}>{user?.name}</h2>
            <div style={S.subtext}>{user?.email}</div>
            <span style={S.badge("green")}>Customer</span>
          </div>
        </div>
        {[["Full Name", user?.name], ["Email Address", user?.email], ["Phone", user?.phone || "+91 98765 43210"], ["City", user?.city || "Mumbai"]].map(([k, v]) => (
          <div key={k} style={{ marginBottom: 14 }}>
            <label style={{ display: "block", fontSize: 13, color: "#9090a8", marginBottom: 4 }}>{k}</label>
            {editing
              ? <input style={S.input} defaultValue={v} />
              : <div style={{ padding: "10px 0", fontWeight: 500 }}>{v}</div>
            }
          </div>
        ))}
        <div style={{ display: "flex", gap: 12 }}>
          <button style={S.btn(editing ? "primary" : "secondary")} onClick={() => setEditing(e => !e)}>{editing ? "Save Changes" : "Edit Profile"}</button>
          {editing && <button style={S.btn("secondary")} onClick={() => setEditing(false)}>Cancel</button>}
        </div>
      </div>
      <div style={{ display: "flex", gap: 12 }}>
        <div style={{ ...S.statsCard, flex: 1, textAlign: "center" }}>
          <div style={{ fontSize: 28, fontWeight: 700, color: "#e85d26" }}>12</div>
          <div style={S.subtext}>Total Bookings</div>
        </div>
        <div style={{ ...S.statsCard, flex: 1, textAlign: "center" }}>
          <div style={{ fontSize: 28, fontWeight: 700, color: "#e85d26" }}>₹4,820</div>
          <div style={S.subtext}>Total Spent</div>
        </div>
        <div style={{ ...S.statsCard, flex: 1, textAlign: "center" }}>
          <div style={{ fontSize: 28, fontWeight: 700, color: "#e85d26" }}>8</div>
          <div style={S.subtext}>Movies Watched</div>
        </div>
      </div>
    </div>
  );
}

function SettingsPage() {
  const [settings, setSettings] = useState({ emailNotif: true, smsNotif: false, twoFactor: false, newsletter: true, darkMode: true, autoplay: false });
  const toggle = k => setSettings(s => ({ ...s, [k]: !s[k] }));

  const Toggle = ({ k }) => (
    <div onClick={() => toggle(k)} style={{ width: 44, height: 24, borderRadius: 12, background: settings[k] ? "#e85d26" : "#2a2a3a", cursor: "pointer", position: "relative", transition: "background 0.2s" }}>
      <div style={{ width: 20, height: 20, borderRadius: "50%", background: "#fff", position: "absolute", top: 2, left: settings[k] ? 22 : 2, transition: "left 0.2s" }} />
    </div>
  );

  return (
    <div style={{ maxWidth: 560 }}>
      <h1 style={S.h1}>Settings</h1>
      {[
        { section: "Notifications", items: [["emailNotif", "Email Notifications", "Receive booking confirmations via email"], ["smsNotif", "SMS Alerts", "Get SMS updates for show reminders"], ["newsletter", "Newsletter", "Monthly movie recommendations"]] },
        { section: "Security", items: [["twoFactor", "Two-Factor Authentication", "Add an extra layer of security"]] },
        { section: "Preferences", items: [["darkMode", "Dark Mode", "Use dark theme across the app"], ["autoplay", "Autoplay Trailers", "Auto-play trailers on movie pages"]] },
      ].map(({ section, items }) => (
        <div key={section} style={{ ...S.card, marginBottom: 16 }}>
          <h2 style={S.h2}>{section}</h2>
          {items.map(([k, label, desc]) => (
            <div key={k} style={{ display: "flex", justifyContent: "space-between", alignItems: "center", padding: "12px 0", borderBottom: "1px solid #1e1e2e" }}>
              <div><div style={{ fontWeight: 500, marginBottom: 2 }}>{label}</div><div style={{ ...S.subtext, fontSize: 12 }}>{desc}</div></div>
              <Toggle k={k} />
            </div>
          ))}
        </div>
      ))}
      <div style={{ ...S.card }}>
        <h2 style={S.h2}>Danger Zone</h2>
        <div style={{ display: "flex", gap: 12 }}>
          <button style={S.btn("danger")}>Delete Account</button>
          <button style={S.btn("secondary")}>Deactivate Account</button>
        </div>
      </div>
    </div>
  );
}

function BookingHistoryPage() {
  return (
    <div>
      <h1 style={S.h1}>Booking History</h1>
      <p style={{ ...S.subtext, marginBottom: 24 }}>All your past and upcoming bookings</p>
      {BOOKING_HISTORY.map(b => (
        <div key={b.id} style={{ ...S.card, marginBottom: 12, display: "flex", justifyContent: "space-between", alignItems: "center", flexWrap: "wrap", gap: 12 }}>
          <div>
            <div style={{ fontWeight: 600, fontSize: 16, marginBottom: 4 }}>{b.movie}</div>
            <div style={{ ...S.subtext, marginBottom: 4 }}>{b.theatre}</div>
            <div style={S.subtext}>{b.date} · {b.time} · Seats: {b.seats.join(", ")}</div>
          </div>
          <div style={{ textAlign: "right" }}>
            <span style={S.badge(b.status === "Confirmed" ? "green" : "red")}>{b.status}</span>
            <div style={{ fontWeight: 700, fontSize: 18, color: "#e85d26", marginTop: 8 }}>₹{b.total}</div>
            <div style={{ fontSize: 12, color: "#9090a8", marginTop: 2 }}>ID: {b.id}</div>
          </div>
        </div>
      ))}
    </div>
  );
}

// ─── OWNER MODULE ─────────────────────────────────────────────────────────────
function OwnerDashboard() {
  const [activeSection, setActiveSection] = useState("overview");
  const { user } = useApp();
  const sideItems = [
    { key: "overview", icon: "📊", label: "Overview" },
    { key: "movies", icon: "🎬", label: "Manage Movies" },
    { key: "shows", icon: "🗓️", label: "Manage Shows" },
    { key: "bookings", icon: "🎟️", label: "View Bookings" },
    { key: "screens", icon: "🖥️", label: "Screen Management" },
    { key: "seatLayout", icon: "💺", label: "Seat Layout" },
  ];

  const renderSection = () => {
    switch (activeSection) {
      case "overview": return <OwnerOverview />;
      case "movies": return <OwnerMovies />;
      case "shows": return <OwnerShows />;
      case "bookings": return <OwnerBookings />;
      case "screens": return <OwnerScreens />;
      case "seatLayout": return <OwnerSeatLayout />;
      default: return null;
    }
  };

  return (
    <div style={S.layout}>
      <Sidebar items={sideItems} activeItem={activeSection} onSelect={setActiveSection} />
      <div style={S.content}>
        <div style={{ marginBottom: 20, padding: "12px 16px", background: "#1a1a26", borderRadius: 8, display: "flex", justifyContent: "space-between", alignItems: "center" }}>
          <span style={{ color: "#9090a8", fontSize: 14 }}>🏢 {user?.theatre || "PVR Cinemas — Juhu"}</span>
          <span style={S.badge("green")}>Approved</span>
        </div>
        {renderSection()}
      </div>
    </div>
  );
}

function OwnerOverview() {
  const stats = [["₹2,84,500", "Revenue This Month", "+12%"], ["1,240", "Tickets Sold", "+8%"], ["3", "Active Screens", ""], ["18", "Shows Today", ""]];
  return (
    <div>
      <h1 style={S.h1}>Theatre Dashboard</h1>
      <div style={{ display: "grid", gridTemplateColumns: "repeat(auto-fill, minmax(180px, 1fr))", gap: 14, marginBottom: 28 }}>
        {stats.map(([val, label, change]) => (
          <div key={label} style={S.statsCard}>
            <div style={{ fontSize: 26, fontWeight: 700, color: "#e85d26" }}>{val}</div>
            <div style={S.subtext}>{label}</div>
            {change && <div style={{ color: "#5dcc7a", fontSize: 12, marginTop: 4 }}>{change} vs last month</div>}
          </div>
        ))}
      </div>
      <h2 style={S.h2}>Today's Shows</h2>
      {OWNER_SHOWS.map(s => (
        <div key={s.id} style={{ ...S.card, marginBottom: 10, display: "flex", justifyContent: "space-between", alignItems: "center" }}>
          <div>
            <div style={{ fontWeight: 600, marginBottom: 4 }}>{s.movie}</div>
            <div style={{ ...S.subtext, marginBottom: 6 }}>{s.screen}</div>
            <div style={{ display: "flex", gap: 8, flexWrap: "wrap" }}>{s.times.map(t => <span key={t} style={S.tag}>{t}</span>)}</div>
          </div>
          <div style={{ textAlign: "right" }}>
            <div style={{ fontSize: 20, fontWeight: 700, color: "#e85d26" }}>{s.bookings}</div>
            <div style={S.subtext}>bookings</div>
          </div>
        </div>
      ))}
    </div>
  );
}

function OwnerMovies() {
  const [editing, setEditing] = useState(null);
  return (
    <div>
      <div style={{ display: "flex", justifyContent: "space-between", alignItems: "center", marginBottom: 20 }}>
        <h1 style={{ ...S.h1, margin: 0 }}>Manage Movies</h1>
        <button style={S.btn("primary")} onClick={() => setEditing({})}>+ Add Movie</button>
      </div>
      {editing !== null && (
        <div style={{ ...S.card, marginBottom: 20, borderColor: "#e85d26" }}>
          <h3 style={S.h3}>{editing.id ? "Edit Movie" : "Add New Movie"}</h3>
          <div style={{ display: "grid", gridTemplateColumns: "1fr 1fr", gap: 14, marginBottom: 16 }}>
            {[["Movie Title", "title"], ["Genre", "genre"], ["Language", "language"], ["Duration", "duration"], ["Director", "director"], ["Release Date", "releaseDate"]].map(([l, k]) => (
              <div key={k}><label style={{ display: "block", fontSize: 13, color: "#9090a8", marginBottom: 4 }}>{l}</label><input style={S.input} defaultValue={editing[k] || ""} /></div>
            ))}
          </div>
          <div style={{ marginBottom: 16 }}><label style={{ display: "block", fontSize: 13, color: "#9090a8", marginBottom: 4 }}>Description</label><textarea style={{ ...S.input, minHeight: 80, resize: "vertical" }} defaultValue={editing.description || ""} /></div>
          <div style={{ display: "flex", gap: 12 }}>
            <button style={S.btn("primary")} onClick={() => setEditing(null)}>Save Movie</button>
            <button style={S.btn("secondary")} onClick={() => setEditing(null)}>Cancel</button>
          </div>
        </div>
      )}
      {MOVIES.slice(0, 5).map(m => (
        <div key={m.id} style={{ ...S.card, marginBottom: 10, display: "flex", justifyContent: "space-between", alignItems: "center" }}>
          <div style={{ display: "flex", gap: 16, alignItems: "center" }}>
            <span style={{ fontSize: 32 }}>{m.poster}</span>
            <div>
              <div style={{ fontWeight: 600 }}>{m.title}</div>
              <div style={S.subtext}>{m.genre} · {m.language} · {m.duration}</div>
              <span style={S.badge(m.status === "Now Showing" ? "green" : "orange")}>{m.status}</span>
            </div>
          </div>
          <div style={{ display: "flex", gap: 8 }}>
            <button style={S.btn("secondary")} onClick={() => setEditing(m)}>Edit</button>
            <button style={S.btn("danger")}>Remove</button>
          </div>
        </div>
      ))}
    </div>
  );
}

function OwnerShows() {
  const [showForm, setShowForm] = useState(false);
  return (
    <div>
      <div style={{ display: "flex", justifyContent: "space-between", alignItems: "center", marginBottom: 20 }}>
        <h1 style={{ ...S.h1, margin: 0 }}>Manage Shows</h1>
        <button style={S.btn("primary")} onClick={() => setShowForm(s => !s)}>+ Add Show</button>
      </div>
      {showForm && (
        <div style={{ ...S.card, marginBottom: 20, borderColor: "#e85d26" }}>
          <h3 style={S.h3}>Create New Show</h3>
          <div style={{ display: "grid", gridTemplateColumns: "1fr 1fr", gap: 14, marginBottom: 16 }}>
            {[["Movie", "select"], ["Screen / Audi", "select"], ["Date", "date"], ["Time", "time"]].map(([l, t]) => (
              <div key={l}><label style={{ display: "block", fontSize: 13, color: "#9090a8", marginBottom: 4 }}>{l}</label>
                {t === "select" ? <select style={S.input}><option>Select...</option></select> : <input style={S.input} type={t} />}
              </div>
            ))}
          </div>
          <div style={{ display: "flex", gap: 12 }}>
            <button style={S.btn("primary")} onClick={() => setShowForm(false)}>Create Show</button>
            <button style={S.btn("secondary")} onClick={() => setShowForm(false)}>Cancel</button>
          </div>
        </div>
      )}
      {OWNER_SHOWS.map(s => (
        <div key={s.id} style={{ ...S.card, marginBottom: 10 }}>
          <div style={{ display: "flex", justifyContent: "space-between", alignItems: "flex-start", marginBottom: 10 }}>
            <div>
              <div style={{ fontWeight: 600, fontSize: 16 }}>{s.movie}</div>
              <div style={S.subtext}>{s.screen} · {s.date}</div>
            </div>
            <div style={{ display: "flex", gap: 8 }}>
              <button style={S.btn("secondary")}>Edit</button>
              <button style={S.btn("danger")}>Cancel Show</button>
            </div>
          </div>
          <div style={{ display: "flex", gap: 8, flexWrap: "wrap" }}>
            {s.times.map(t => <span key={t} style={{ ...S.tag, background: "#1e2e1e", color: "#5dcc7a" }}>{t}</span>)}
          </div>
        </div>
      ))}
    </div>
  );
}

function OwnerBookings() {
  const ownerBookings = [
    { id: "BK001", customer: "Ananya Sharma", movie: "Stellar Odyssey", time: "6:00 PM", seats: ["F5", "F6"], amount: 640 },
    { id: "BK002", customer: "Meera Pillai", movie: "Echoes of the Past", time: "9:00 PM", seats: ["C3", "C4"], amount: 560 },
    { id: "BK003", customer: "Kabir Singh", movie: "Iron Citadel", time: "3:30 PM", seats: ["A1"], amount: 200 },
    { id: "BK004", customer: "Priya Nair", movie: "Stellar Odyssey", time: "10:00 AM", seats: ["D7", "D8", "D9"], amount: 960 },
  ];
  return (
    <div>
      <h1 style={S.h1}>View Bookings</h1>
      <div style={{ display: "grid", gridTemplateColumns: "repeat(3,1fr)", gap: 12, marginBottom: 24 }}>
        {[["142", "Total Today"], ["₹45,280", "Revenue Today"], ["89%", "Occupancy"]].map(([v, l]) => (
          <div key={l} style={S.statsCard}><div style={{ fontSize: 22, fontWeight: 700, color: "#e85d26" }}>{v}</div><div style={S.subtext}>{l}</div></div>
        ))}
      </div>
      <table style={{ width: "100%", borderCollapse: "collapse", fontSize: 14 }}>
        <thead><tr style={{ borderBottom: "1px solid #2a2a3a" }}>
          {["Booking ID", "Customer", "Movie", "Show Time", "Seats", "Amount"].map(h => <th key={h} style={{ padding: "10px 12px", textAlign: "left", color: "#9090a8", fontWeight: 500 }}>{h}</th>)}
        </tr></thead>
        <tbody>{ownerBookings.map(b => (
          <tr key={b.id} style={{ borderBottom: "1px solid #1e1e2e" }}>
            <td style={{ padding: "12px" }}><span style={{ color: "#e85d26", fontWeight: 500 }}>{b.id}</span></td>
            <td style={{ padding: "12px" }}>{b.customer}</td>
            <td style={{ padding: "12px" }}>{b.movie}</td>
            <td style={{ padding: "12px" }}>{b.time}</td>
            <td style={{ padding: "12px" }}>{b.seats.join(", ")}</td>
            <td style={{ padding: "12px", fontWeight: 600 }}>₹{b.amount}</td>
          </tr>
        ))}</tbody>
      </table>
    </div>
  );
}

function OwnerScreens() {
  return (
    <div>
      <div style={{ display: "flex", justifyContent: "space-between", alignItems: "center", marginBottom: 20 }}>
        <h1 style={{ ...S.h1, margin: 0 }}>Screen Management</h1>
        <button style={S.btn("primary")}>+ Add Screen</button>
      </div>
      {SCREENS.map(s => (
        <div key={s.id} style={{ ...S.card, marginBottom: 12, display: "flex", justifyContent: "space-between", alignItems: "center" }}>
          <div>
            <div style={{ fontWeight: 600, fontSize: 16, marginBottom: 4 }}>{s.name}</div>
            <div style={S.subtext}>Capacity: {s.capacity} seats</div>
            <div style={{ display: "flex", gap: 8, marginTop: 8, flexWrap: "wrap" }}>{s.features.map(f => <span key={f} style={S.tag}>{f}</span>)}</div>
          </div>
          <div style={{ display: "flex", gap: 8 }}>
            <span style={S.badge("green")}>Active</span>
            <button style={S.btn("secondary")}>Edit</button>
          </div>
        </div>
      ))}
    </div>
  );
}

function OwnerSeatLayout() {
  const rows = ["A", "B", "C", "D", "E", "F"];
  const cols = Array.from({ length: 10 }, (_, i) => i + 1);
  const [layout, setLayout] = useState({});
  const types = { normal: "#1e1e2e", premium: "#2a1a0a", vip: "#2a0a0a", blocked: "#0a0a0a" };
  const [brushType, setBrushType] = useState("normal");

  const toggle = (seat) => setLayout(l => ({ ...l, [seat]: brushType }));

  return (
    <div>
      <h1 style={S.h1}>Seat Layout Configuration</h1>
      <div style={{ ...S.card, marginBottom: 16 }}>
        <div style={{ marginBottom: 12 }}>
          <span style={{ ...S.subtext, marginRight: 12 }}>Select seat type to paint:</span>
          {Object.entries({ normal: "Standard", premium: "Premium", vip: "VIP", blocked: "Blocked" }).map(([k, label]) => (
            <button key={k} onClick={() => setBrushType(k)}
              style={{ ...S.btn(brushType === k ? "primary" : "secondary"), marginRight: 8, marginBottom: 8 }}>{label}</button>
          ))}
        </div>
        <div style={{ overflowX: "auto" }}>
          <div style={{ textAlign: "center", background: "#e85d26", borderRadius: "32px 32px 4px 4px", padding: "6px 0", maxWidth: 420, margin: "0 auto 20px" }}><span style={{ fontSize: 12 }}>SCREEN</span></div>
          {rows.map(row => (
            <div key={row} style={{ display: "flex", alignItems: "center", gap: 6, marginBottom: 6, justifyContent: "center" }}>
              <span style={{ width: 20, fontSize: 12, color: "#9090a8" }}>{row}</span>
              {cols.map(col => {
                const seat = `${row}${col}`;
                const type = layout[seat] || "normal";
                return <div key={col} style={{ width: 32, height: 32, borderRadius: 4, background: types[type], border: "1px solid #3a3a4a", cursor: "pointer", display: "flex", alignItems: "center", justifyContent: "center", fontSize: 10, color: "#9090a8" }}
                  onClick={() => toggle(seat)}>{col}</div>;
              })}
            </div>
          ))}
        </div>
      </div>
      <div style={{ display: "flex", gap: 8 }}>
        <button style={S.btn("primary")}>Save Layout</button>
        <button style={S.btn("secondary")} onClick={() => setLayout({})}>Reset</button>
      </div>
    </div>
  );
}

// ─── ADMIN MODULE ─────────────────────────────────────────────────────────────
function AdminDashboard() {
  const [activeSection, setActiveSection] = useState("overview");
  const sideItems = [
    { key: "overview", icon: "📊", label: "System Overview" },
    { key: "users", icon: "👥", label: "Manage Users" },
    { key: "theatres", icon: "🏢", label: "Manage Theatres" },
    { key: "requests", icon: "📋", label: "Theatre Requests" },
    { key: "reports", icon: "📈", label: "Reports" },
  ];
  const renderSection = () => {
    switch (activeSection) {
      case "overview": return <AdminOverview />;
      case "users": return <AdminUsers />;
      case "theatres": return <AdminTheatres />;
      case "requests": return <AdminRequests />;
      case "reports": return <AdminReports />;
      default: return null;
    }
  };
  return (
    <div style={S.layout}>
      <Sidebar items={sideItems} activeItem={activeSection} onSelect={setActiveSection} />
      <div style={S.content}>{renderSection()}</div>
    </div>
  );
}

function AdminOverview() {
  const stats = [["8,420", "Total Users", "+5% this week"], ["24", "Active Theatres", "+2 this month"], ["1,28,450", "Total Bookings", "All time"], ["₹4.2Cr", "Total Revenue", "This year"]];
  return (
    <div>
      <h1 style={S.h1}>System Overview</h1>
      <div style={{ display: "grid", gridTemplateColumns: "repeat(auto-fill, minmax(180px, 1fr))", gap: 14, marginBottom: 28 }}>
        {stats.map(([v, l, s]) => (
          <div key={l} style={S.statsCard}>
            <div style={{ fontSize: 26, fontWeight: 700, color: "#e85d26" }}>{v}</div>
            <div style={S.subtext}>{l}</div>
            <div style={{ fontSize: 12, color: "#5dcc7a", marginTop: 4 }}>{s}</div>
          </div>
        ))}
      </div>
      <div style={{ display: "grid", gridTemplateColumns: "1fr 1fr", gap: 16 }}>
        <div style={S.card}>
          <h3 style={S.h3}>Pending Actions</h3>
          {[["2 theatre approval requests", "orange"], ["1 dispute resolution pending", "red"], ["5 new user reports", "orange"]].map(([t, c]) => (
            <div key={t} style={{ display: "flex", justifyContent: "space-between", padding: "8px 0", borderBottom: "1px solid #1e1e2e", fontSize: 14 }}>
              <span>{t}</span><span style={S.badge(c)}>Action</span>
            </div>
          ))}
        </div>
        <div style={S.card}>
          <h3 style={S.h3}>Top Cities by Bookings</h3>
          {[["Mumbai", 42], ["Delhi", 28], ["Bengaluru", 18], ["Hyderabad", 12]].map(([city, pct]) => (
            <div key={city} style={{ marginBottom: 12 }}>
              <div style={{ display: "flex", justifyContent: "space-between", fontSize: 14, marginBottom: 4 }}><span>{city}</span><span style={{ color: "#e85d26" }}>{pct}%</span></div>
              <div style={{ height: 6, background: "#1e1e2e", borderRadius: 3 }}><div style={{ height: "100%", width: `${pct}%`, background: "#e85d26", borderRadius: 3 }} /></div>
            </div>
          ))}
        </div>
      </div>
    </div>
  );
}

function AdminUsers() {
  const [search, setSearch] = useState("");
  const [modal, setModal] = useState(null);
  const filtered = ADMIN_USERS.filter(u => u.name.toLowerCase().includes(search.toLowerCase()) || u.email.includes(search));
  return (
    <div>
      <div style={{ display: "flex", justifyContent: "space-between", alignItems: "center", marginBottom: 20 }}>
        <h1 style={{ ...S.h1, margin: 0 }}>Manage Users</h1>
        <input style={{ ...S.input, maxWidth: 280 }} placeholder="Search users..." value={search} onChange={e => setSearch(e.target.value)} />
      </div>
      <table style={{ width: "100%", borderCollapse: "collapse", fontSize: 14 }}>
        <thead><tr style={{ borderBottom: "1px solid #2a2a3a" }}>
          {["Name", "Email", "Role", "Joined", "Bookings", "Status", "Actions"].map(h => <th key={h} style={{ padding: "10px 12px", textAlign: "left", color: "#9090a8", fontWeight: 500 }}>{h}</th>)}
        </tr></thead>
        <tbody>{filtered.map(u => (
          <tr key={u.id} style={{ borderBottom: "1px solid #1e1e2e" }}>
            <td style={{ padding: "12px" }}>{u.name}</td>
            <td style={{ padding: "12px", color: "#9090a8" }}>{u.email}</td>
            <td style={{ padding: "12px" }}><span style={S.tag}>{u.role}</span></td>
            <td style={{ padding: "12px", color: "#9090a8" }}>{u.joined}</td>
            <td style={{ padding: "12px" }}>{u.bookings}</td>
            <td style={{ padding: "12px" }}><span style={S.badge(u.status === "Active" ? "green" : "orange")}>{u.status}</span></td>
            <td style={{ padding: "12px" }}>
              <button style={{ ...S.btn("secondary"), padding: "4px 10px", fontSize: 12, marginRight: 4 }} onClick={() => setModal(u)}>View</button>
              <button style={{ ...S.btn("danger"), padding: "4px 10px", fontSize: 12 }}>Block</button>
            </td>
          </tr>
        ))}</tbody>
      </table>
      {modal && (
        <Modal title="User Details" onClose={() => setModal(null)}>
          <div style={{ display: "flex", gap: 16, alignItems: "center", marginBottom: 20 }}>
            <div style={{ width: 48, height: 48, borderRadius: "50%", background: "#e85d26", display: "flex", alignItems: "center", justifyContent: "center", fontWeight: 700 }}>{modal.name[0]}</div>
            <div><div style={{ fontWeight: 600, fontSize: 16 }}>{modal.name}</div><div style={S.subtext}>{modal.email}</div></div>
          </div>
          {[["Role", modal.role], ["Joined", modal.joined], ["Total Bookings", modal.bookings], ["Status", modal.status]].map(([k, v]) => (
            <div key={k} style={{ display: "flex", justifyContent: "space-between", padding: "8px 0", borderBottom: "1px solid #1e1e2e" }}>
              <span style={S.subtext}>{k}</span><span style={{ fontWeight: 500 }}>{v}</span>
            </div>
          ))}
        </Modal>
      )}
    </div>
  );
}

function AdminTheatres() {
  return (
    <div>
      <h1 style={S.h1}>Manage Theatres</h1>
      {ADMIN_THEATRES.map(t => (
        <div key={t.id} style={{ ...S.card, marginBottom: 12, display: "flex", justifyContent: "space-between", alignItems: "center" }}>
          <div>
            <div style={{ fontWeight: 600, fontSize: 16, marginBottom: 4 }}>{t.name}</div>
            <div style={S.subtext}>{t.city} · Owner: {t.owner}</div>
            <div style={{ marginTop: 6 }}>
              <span style={S.tag}>{t.screens} Screens</span>
            </div>
          </div>
          <div style={{ display: "flex", flexDirection: "column", alignItems: "flex-end", gap: 10 }}>
            <span style={S.badge(t.status === "Approved" ? "green" : "orange")}>{t.status}</span>
            <div style={{ display: "flex", gap: 8 }}>
              <button style={S.btn("secondary")}>View Details</button>
              {t.status === "Approved" && <button style={S.btn("danger")}>Suspend</button>}
            </div>
          </div>
        </div>
      ))}
    </div>
  );
}

function AdminRequests() {
  const [requests, setRequests] = useState(ADMIN_THEATRES.filter(t => t.status === "Pending"));
  const handleAction = (id, action) => setRequests(r => r.filter(t => t.id !== id));

  return (
    <div>
      <h1 style={S.h1}>Theatre Approval Requests</h1>
      <p style={{ ...S.subtext, marginBottom: 24 }}>{requests.length} pending request(s)</p>
      {requests.length === 0 && (
        <div style={{ ...S.card, textAlign: "center", padding: "48px 24px" }}>
          <div style={{ fontSize: 48, marginBottom: 12 }}>✅</div>
          <div style={{ fontWeight: 500 }}>All requests have been processed</div>
        </div>
      )}
      {requests.map(t => (
        <div key={t.id} style={{ ...S.card, marginBottom: 16, borderColor: "#e89444" }}>
          <div style={{ display: "flex", justifyContent: "space-between", alignItems: "flex-start", marginBottom: 14 }}>
            <div>
              <h3 style={S.h3}>{t.name}</h3>
              <div style={S.subtext}>Owner: {t.owner} · City: {t.city}</div>
              <div style={{ marginTop: 6 }}><span style={S.tag}>{t.screens} screens planned</span></div>
            </div>
            <span style={S.badge("orange")}>Pending Review</span>
          </div>
          <div style={{ display: "flex", gap: 12 }}>
            <button style={{ ...S.btn("primary"), background: "#1a3a1a", color: "#5dcc7a" }} onClick={() => handleAction(t.id, "approve")}>✓ Approve</button>
            <button style={{ ...S.btn("danger") }} onClick={() => handleAction(t.id, "reject")}>✕ Reject</button>
            <button style={S.btn("secondary")}>Request More Info</button>
          </div>
        </div>
      ))}
    </div>
  );
}

function AdminReports() {
  const data = [
    { month: "Jan", bookings: 8420, revenue: 1684000 },
    { month: "Feb", bookings: 9200, revenue: 1840000 },
    { month: "Mar", bookings: 11000, revenue: 2200000 },
    { month: "Apr", bookings: 10500, revenue: 2100000 },
    { month: "May", bookings: 12800, revenue: 2560000 },
    { month: "Jun", bookings: 11200, revenue: 2240000 },
  ];
  const maxBookings = Math.max(...data.map(d => d.bookings));

  return (
    <div>
      <h1 style={S.h1}>Reports & Analytics</h1>
      <div style={{ display: "grid", gridTemplateColumns: "repeat(3,1fr)", gap: 14, marginBottom: 24 }}>
        {[["62,120", "Total Bookings (6 mo)"], ["₹1.26Cr", "Total Revenue (6 mo)"], ["4.2/5", "Avg. Rating"]].map(([v, l]) => (
          <div key={l} style={S.statsCard}><div style={{ fontSize: 24, fontWeight: 700, color: "#e85d26" }}>{v}</div><div style={S.subtext}>{l}</div></div>
        ))}
      </div>
      <div style={{ ...S.card, marginBottom: 20 }}>
        <h3 style={S.h3}>Monthly Bookings</h3>
        <div style={{ display: "flex", alignItems: "flex-end", gap: 12, height: 160, paddingTop: 16 }}>
          {data.map(d => (
            <div key={d.month} style={{ flex: 1, display: "flex", flexDirection: "column", alignItems: "center", gap: 6 }}>
              <div style={{ fontSize: 11, color: "#9090a8" }}>{(d.bookings / 1000).toFixed(1)}k</div>
              <div style={{ width: "100%", background: "#e85d26", borderRadius: "4px 4px 0 0", height: `${(d.bookings / maxBookings) * 120}px` }} />
              <div style={{ fontSize: 12, color: "#9090a8" }}>{d.month}</div>
            </div>
          ))}
        </div>
      </div>
      <div style={{ display: "grid", gridTemplateColumns: "1fr 1fr", gap: 14 }}>
        <div style={S.card}>
          <h3 style={S.h3}>Top Movies</h3>
          {MOVIES.slice(0, 4).map((m, i) => (
            <div key={m.id} style={{ display: "flex", justifyContent: "space-between", padding: "8px 0", borderBottom: "1px solid #1e1e2e", fontSize: 14 }}>
              <span><span style={{ color: "#e85d26", marginRight: 8 }}>{i + 1}.</span>{m.title}</span>
              <span style={{ color: "#9090a8" }}>★ {m.rating}</span>
            </div>
          ))}
        </div>
        <div style={S.card}>
          <h3 style={S.h3}>Top Theatres</h3>
          {ADMIN_THEATRES.filter(t => t.status === "Approved").map((t, i) => (
            <div key={t.id} style={{ display: "flex", justifyContent: "space-between", padding: "8px 0", borderBottom: "1px solid #1e1e2e", fontSize: 14 }}>
              <span><span style={{ color: "#e85d26", marginRight: 8 }}>{i + 1}.</span>{t.name}</span>
              <span style={S.tag}>{t.city}</span>
            </div>
          ))}
        </div>
      </div>
    </div>
  );
}

// ─── ROOT APP ─────────────────────────────────────────────────────────────────
export default function App() {
  const [screen, setScreen] = useState("login");
  const [user, setUser] = useState(null);
  const [booking, setBooking] = useState({});

  const renderScreen = () => {
    switch (screen) {
      case "login": return <LoginPage />;
      case "signup": return <SignupPage />;
      case "home": return <HomePage />;
      case "movieDetail": return <MovieDetailPage />;
      case "locationSelect": return <LocationSelectPage />;
      case "theatreSelect": return <TheatreSelectPage />;
      case "screenSelect": return <ScreenSelectPage />;
      case "showtimeSelect": return <ShowtimeSelectPage />;
      case "seatSelect": return <SeatSelectPage />;
      case "bookingSummary": return <BookingSummaryPage />;
      case "bookingConfirm": return <BookingConfirmPage />;
      case "profile": return <ProfilePage />;
      case "settings": return <SettingsPage />;
      case "history": return <BookingHistoryPage />;
      case "ownerDash": return <OwnerDashboard />;
      case "adminDash": return <AdminDashboard />;
      default: return <LoginPage />;
    }
  };

  const showNavbar = screen !== "login" && screen !== "signup";
  const isFullLayout = screen === "ownerDash" || screen === "adminDash";

  return (
    <AppContext.Provider value={{ screen, setScreen, user, setUser, booking, setBooking }}>
      <div style={S.app}>
        {showNavbar && <Navbar />}
        {isFullLayout
          ? renderScreen()
          : <div style={{ padding: ["login", "signup"].includes(screen) ? 0 : "28px 32px", maxWidth: ["login", "signup"].includes(screen) ? "none" : 1100, margin: "0 auto" }}>
              {renderScreen()}
            </div>
        }
      </div>
    </AppContext.Provider>
  );
}
Stack
