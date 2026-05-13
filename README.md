
export default function Home() {
  const products = [
    { name: "Midnight Oud", price: 25000, commission: 5000 },
    { name: "Veloura Gold", price: 40000, commission: 8000 },
    { name: "Aura Fresh", price: 20000, commission: 4000 }
  ];

  const sellers = [
    { name: "Amina", sales: 62, earnings: 620000 },
    { name: "Brian", sales: 51, earnings: 510000 },
    { name: "Shakira", sales: 44, earnings: 440000 }
  ];

  function aiRecommend(text) {
    if (!text) return "Veloura Gold";
    if (text.toLowerCase().includes("luxury")) return "Midnight Oud";
    if (text.toLowerCase().includes("fresh")) return "Aura Fresh";
    return "Veloura Gold";
  }

  const recommendation = aiRecommend("luxury perfume");

  return (
    <div style={{ fontFamily: "Arial", background: "#0a0a0a", color: "white", minHeight: "100vh", padding: 20 }}>

      {/* HEADER */}
      <h1 style={{ color: "#ff4fd8", fontSize: 40 }}>
        Essence Connect
      </h1>

      <p style={{ color: "#aaa", marginBottom: 30 }}>
        AI-powered fragrance selling & connected marketing system
      </p>

      {/* AI SECTION */}
      <div style={{ background: "#111", padding: 15, borderRadius: 10, marginBottom: 30 }}>
        <h2>AI Recommendation</h2>
        <p>Suggested for customers: <b style={{ color: "#ff4fd8" }}>{recommendation}</b></p>
      </div>

      {/* PRODUCTS */}
      <h2>Products</h2>
      <div style={{ display: "grid", gap: 15, gridTemplateColumns: "repeat(auto-fit, minmax(220px, 1fr))" }}>
        {products.map((p) => (
          <div key={p.name} style={{ background: "#111", padding: 15, borderRadius: 10 }}>
            <h3>{p.name}</h3>
            <p>Price: UGX {p.price}</p>
            <p style={{ color: "lightgreen" }}>Commission: UGX {p.commission}</p>

            <a
              href={`https://wa.me/?text=I want ${p.name} - UGX ${p.price}`}
              style={{
                display: "inline-block",
                marginTop: 10,
                background: "#ff4fd8",
                padding: "8px 12px",
                borderRadius: 8,
                color: "white",
                textDecoration: "none"
              }}
            >
              Order on WhatsApp
            </a>
          </div>
        ))}
      </div>

      {/* SELLER LEADERBOARD */}
      <h2 style={{ marginTop: 40 }}>Top Sellers</h2>
      <div style={{ display: "grid", gap: 10 }}>
        {sellers.map((s) => (
          <div key={s.name} style={{ background: "#111", padding: 15, borderRadius: 10 }}>
            <b>{s.name}</b>
            <p>Sales: {s.sales}</p>
            <p style={{ color: "lightgreen" }}>Earnings: UGX {s.earnings}</p>
          </div>
        ))}
      </div>

      {/* HOW IT WORKS */}
      <div style={{ marginTop: 40, padding: 15, background: "#111", borderRadius: 10 }}>
        <h2>How It Works</h2>
        <p>
          Sellers promote perfumes → Customers order via WhatsApp →
          You earn commission → System tracks performance (MVP version)
        </p>
      </div>

      {/* FOOTER */}
      <p style={{ marginTop: 50, color: "#555", fontSize: 12 }}>
        Essence Connect MVP — Built for scalable fragrance commerce
      </p>
    </div>
  );
}
