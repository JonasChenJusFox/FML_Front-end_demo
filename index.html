/*
   NYBites
   Main front-end behavior
*/

/* ---------- Shared helpers ---------- */
const pageState = {
  view: "grid"
};

function $(selector) {
  return document.querySelector(selector);
}

function $all(selector) {
  return Array.from(document.querySelectorAll(selector));
}

function setText(id, value) {
  const element = document.getElementById(id);
  if (element) {
    element.textContent = value;
  }
}

function escapeHtml(value) {
  return String(value)
    .replaceAll("&", "&amp;")
    .replaceAll("<", "&lt;")
    .replaceAll(">", "&gt;")
    .replaceAll('"', "&quot;")
    .replaceAll("'", "&#039;");
}

/* ---------- Storage keys ---------- */
const STORAGE_KEYS = {
  profile: "NYBites.profile",
  saved: "NYBites.saved",
  visited: "NYBites.visited"
};

/* ---------- Storage access ---------- */
function getProfile() {
  const raw = localStorage.getItem(STORAGE_KEYS.profile);
  return raw ? JSON.parse(raw) : {
    cuisines: ["Chinese", "Indian", "Cafe"],
    vibes: ["quiet", "cozy", "spicy"],
    dietary: ["vegetarian"],
    radius: 20,
    priceLevel: "$$"
  };
}

function saveProfile(profile) {
  localStorage.setItem(STORAGE_KEYS.profile, JSON.stringify(profile));
}

function getSaved() {
  const raw = localStorage.getItem(STORAGE_KEYS.saved);
  return raw ? JSON.parse(raw) : [
    {
      id: 6,
      name: "Saffron Quiet",
      cuisine: "Indian",
      neighborhood: "East Village",
      distanceMin: 11,
      rating: 4.7
    },
    {
      id: 4,
      name: "Studio Sips Café",
      cuisine: "Cafe",
      neighborhood: "SoHo",
      distanceMin: 9,
      rating: 4.4
    }
  ];
}

function saveSaved(saved) {
  localStorage.setItem(STORAGE_KEYS.saved, JSON.stringify(saved));
}

function getVisited() {
  const raw = localStorage.getItem(STORAGE_KEYS.visited);
  return raw ? JSON.parse(raw) : [
    {
      id: 11,
      name: "Canal Heatpot",
      cuisine: "Chinese",
      neighborhood: "Chinatown",
      visitedDate: "3/13/2026",
      tag: "group-friendly"
    },
    {
      id: 1,
      name: "Luna Noodles",
      cuisine: "Chinese",
      neighborhood: "Greenwich Village",
      visitedDate: "3/12/2026",
      tag: "spicy"
    },
    {
      id: 6,
      name: "Saffron Quiet",
      cuisine: "Indian",
      neighborhood: "East Village",
      visitedDate: "3/11/2026",
      tag: "cozy"
    },
    {
      id: 4,
      name: "Studio Sips Café",
      cuisine: "Cafe",
      neighborhood: "SoHo",
      visitedDate: "3/10/2026",
      tag: "study"
    }
  ];
}

function saveVisited(visited) {
  localStorage.setItem(STORAGE_KEYS.visited, JSON.stringify(visited));
}

function seedDemoData() {
  localStorage.removeItem(STORAGE_KEYS.profile);
  localStorage.removeItem(STORAGE_KEYS.saved);
  localStorage.removeItem(STORAGE_KEYS.visited);
  location.reload();
}

function resetDemoData() {
  localStorage.removeItem(STORAGE_KEYS.profile);
  localStorage.removeItem(STORAGE_KEYS.saved);
  localStorage.removeItem(STORAGE_KEYS.visited);
  location.reload();
}

/* ---------- Common UI ---------- */
function renderProfileTags(containerId) {
  const container = document.getElementById(containerId);
  if (!container) return;

  const profile = getProfile();
  const tags = [
    ...profile.cuisines,
    ...profile.vibes,
    ...profile.dietary,
    `${profile.radius} min radius`
  ];

  container.innerHTML = tags
    .map((tag) => `<span class="tag-chip">${escapeHtml(tag)}</span>`)
    .join("");
}

function bindGlobalButtons() {
  $all("[data-seed-demo='true']").forEach((button) => {
    button.addEventListener("click", seedDemoData);
  });

  $all("[data-reset-demo='true']").forEach((button) => {
    button.addEventListener("click", resetDemoData);
  });
}

function bindHamburger() {
  const hamburgerBtn = document.getElementById("hamburgerBtn");
  const mobileMenu = document.getElementById("mobileMenu");

  if (!hamburgerBtn || !mobileMenu) return;

  hamburgerBtn.addEventListener("click", () => {
    const isOpen = mobileMenu.classList.toggle("open");
    hamburgerBtn.setAttribute("aria-expanded", String(isOpen));
  });
}

function renderFooterYear() {
  $all("[data-year]").forEach((node) => {
    node.textContent = new Date().getFullYear();
  });
}

/* ---------- Homepage ---------- */
function renderStarterFeed() {
  const starterFeed = document.getElementById("starterFeed");
  if (!starterFeed) return;

  starterFeed.innerHTML = HOME_STARTER_FEED.map((item) => `
    <article class="feed-card">
      <strong>${escapeHtml(item.title)}</strong>
      <p>${escapeHtml(item.restaurant)}</p>
      <span class="feed-meta">${escapeHtml(item.meta)}</span>
    </article>
  `).join("");
}

function renderSavedCuisineChart() {
  const container = document.getElementById("favoritesByCuisine");
  if (!container) return;

  const maxCount = Math.max(...HOME_SAVED_CUISINES.map((item) => item.count));

  container.innerHTML = HOME_SAVED_CUISINES.map((item) => `
    <div class="mini-row-chart">
      <div class="mini-row-head">
        <strong>${escapeHtml(item.cuisine)}</strong>
        <span>${item.count}</span>
      </div>
      <div class="mini-row-track">
        <div class="mini-row-fill" style="width:${(item.count / maxCount) * 100}%"></div>
      </div>
    </div>
  `).join("");
}

function renderTrafficChart(targetId, restaurant) {
  const target = document.getElementById(targetId);
  if (!target || !restaurant || !restaurant.traffic) return;

  const maxValue = Math.max(...restaurant.traffic);

  target.innerHTML = `
    <div class="traffic-bars">
      ${restaurant.traffic.map((value, index) => {
        const height = Math.max(12, (value / maxValue) * 140);
        return `
          <div class="traffic-bar-group">
            <div class="traffic-bar" style="height:${height}px;"></div>
            <span class="traffic-label">${TRAFFIC_LABELS[index] || ""}</span>
          </div>
        `;
      }).join("")}
    </div>
  `;
}

function updateTrafficSection(restaurantKey) {
  const restaurant = HOME_TRAFFIC_RESTAURANTS[restaurantKey];
  if (!restaurant) return;

  setText(
    "trafficMeta",
    `${restaurant.neighborhood} · ${restaurant.cuisine} · predicted daily traffic pattern`
  );

  renderTrafficChart("trafficChart", restaurant);

  const peakValue = Math.max(...restaurant.traffic);
  const peakIndex = restaurant.traffic.findIndex((value) => value === peakValue);

  const topMoments = document.getElementById("topMoments");
  if (topMoments) {
    topMoments.innerHTML = `
      <div class="insight-chip">Peak hour: ${TRAFFIC_LABELS[peakIndex]}</div>
      <div class="insight-chip">Rating: ${restaurant.rating.toFixed(1)}</div>
      <div class="insight-chip">Distance: ${restaurant.distanceMin} min</div>
    `;
  }
}

function renderHomePage() {
  const saved = getSaved();
  const visited = getVisited();

  setText("metricSaved", String(saved.length));
  setText("metricVisited", String(visited.length));

  const avg = saved.length
    ? (saved.reduce((sum, item) => sum + item.rating, 0) / saved.length).toFixed(1)
    : "0.0";
  setText("metricAverageRating", avg);

  renderProfileTags("homeProfileTags");
  renderStarterFeed();
  renderSavedCuisineChart();

  const trafficSelect = document.getElementById("trafficRestaurantSelect");
  if (trafficSelect) {
    updateTrafficSection(trafficSelect.value);
    trafficSelect.addEventListener("change", function () {
      updateTrafficSection(this.value);
    });
  }
}

/* ---------- Discover ---------- */
function matchesProfile(restaurant, profile) {
  let score = 0;
  if (profile.cuisines.includes(restaurant.cuisine)) score += 3;
  if (restaurant.diets.some((diet) => profile.dietary.includes(diet))) score += 2;
  if (restaurant.vibes.some((vibe) => profile.vibes.includes(vibe))) score += 2;
  if (restaurant.distanceMin <= profile.radius) score += 2;
  score += restaurant.rating;
  return score;
}

function renderDiscoverCards(restaurants) {
  const container = document.getElementById("recommendations");
  if (!container) return;

  container.className =
    pageState.view === "grid"
      ? "results-grid top-space-md"
      : "results-list top-space-md";

  if (!restaurants.length) {
    container.innerHTML = `
      <div class="empty-state">
        No restaurants match your current filters.
      </div>
    `;
    return;
  }

  container.innerHTML = restaurants.map((restaurant) => `
    <article class="restaurant-card">
      <div class="card-top">
        <div>
          <h3>${escapeHtml(restaurant.name)}</h3>
          <p>${escapeHtml(restaurant.description)}</p>
        </div>
        <div class="rating-badge">${restaurant.rating.toFixed(1)}</div>
      </div>

      <div class="meta-line">
        <span>${escapeHtml(restaurant.cuisine)}</span>
        <span>•</span>
        <span>${escapeHtml(restaurant.neighborhood)}</span>
        <span>•</span>
        <span>${restaurant.distanceMin} min</span>
        <span>•</span>
        <span>${"$".repeat(restaurant.priceTier)}</span>
      </div>

      <div class="tag-row">
        ${restaurant.vibes.map((tag) => `
          <span class="tag-chip">${escapeHtml(tag)}</span>
        `).join("")}
      </div>
    </article>
  `).join("");
}

function renderDiscoverMap(restaurants) {
  const map = document.getElementById("mapMarkers");
  if (!map) return;

  map.innerHTML = restaurants.slice(0, 8).map((restaurant) => `
    <div class="marker" style="left:${restaurant.x}%; top:${restaurant.y}%;">
      <div class="marker-label">${escapeHtml(restaurant.name)}</div>
      <div class="marker-pin"></div>
    </div>
  `).join("");
}

function matchesProfile(restaurant, profile) {
  let score = 0;

  if (profile.cuisines.includes(restaurant.cuisine)) score += 3;
  if (restaurant.vibes.some((vibe) => profile.vibes.includes(vibe))) score += 2;
  if (restaurant.diets.some((diet) => profile.dietary.includes(diet))) score += 2;
  if (restaurant.distanceMin <= profile.radius) score += 2;
  score += restaurant.rating;

  return score;
}

function renderDiscoverMap(restaurants) {
  const map = document.getElementById("mapMarkers");
  if (!map) return;

  map.innerHTML = restaurants.slice(0, 8).map((restaurant) => `
    <div class="marker" style="left:${restaurant.x}%; top:${restaurant.y}%;">
      <div class="marker-label">${escapeHtml(restaurant.name)}</div>
      <div class="marker-pin"></div>
    </div>
  `).join("");
}

function renderDiscoverPage() {
  const profile = getProfile();
  const gridButton = document.getElementById("gridViewBtn");
  const listButton = document.getElementById("listViewBtn");

  const ranked = [...RESTAURANTS]
    .map((restaurant) => ({
      ...restaurant,
      score: matchesProfile(restaurant, profile)
    }))
    .sort((a, b) => b.score - a.score);

  function updateDiscoverView() {
    const matchCount = document.getElementById("discoverMatchCount");
    if (matchCount) {
      matchCount.textContent = String(ranked.length);
    }

    const summary = document.getElementById("resultsSummary");
    if (summary) {
      summary.textContent = "Ranked list for your current preferences and search intent.";
    }

    renderDiscoverCards(ranked);
    renderDiscoverMap(ranked);

    if (gridButton) {
      gridButton.classList.toggle("active", pageState.view === "grid");
    }

    if (listButton) {
      listButton.classList.toggle("active", pageState.view === "list");
    }
  }

  if (gridButton) {
    gridButton.addEventListener("click", () => {
      pageState.view = "grid";
      updateDiscoverView();
    });
  }

  if (listButton) {
    listButton.addEventListener("click", () => {
      pageState.view = "list";
      updateDiscoverView();
    });
  }

  updateDiscoverView();
}

/* ---------- Profile ---------- */
function renderSavedRestaurants() {
  const container = document.getElementById("savedList") || document.getElementById("savedRestaurants");
  if (!container) return;

  const saved = getSaved();

  container.innerHTML = saved.map((restaurant) => `
    <article class="list-card">
      <strong>${escapeHtml(restaurant.name)}</strong>
      <p>${escapeHtml(restaurant.cuisine)} · ${escapeHtml(restaurant.neighborhood)} · ${restaurant.distanceMin} min</p>
    </article>
  `).join("");
}

function renderVisitHistory() {
  const container = document.getElementById("historyList") || document.getElementById("visitHistory");
  if (!container) return;

  const visited = getVisited();

  container.innerHTML = visited.map((item) => `
    <article class="history-card">
      <div class="history-main">
        <strong>${escapeHtml(item.name)}</strong>
        <p>${escapeHtml(item.cuisine)} · ${escapeHtml(item.neighborhood)} · visited ${escapeHtml(item.visitedDate)}</p>
      </div>
      <span class="history-tag">${escapeHtml(item.tag)}</span>
    </article>
  `).join("");
}

function setupProfileModal() {
  const openBtn = document.getElementById("openProfileEditorBtn");
  const closeBtn = document.getElementById("closeProfileEditorBtn");
  const modal = document.getElementById("profileEditorModal");
  const saveBtn = document.getElementById("saveProfileBtn");

  if (!openBtn || !modal) return;

  openBtn.addEventListener("click", () => {
    modal.classList.add("open");
    document.body.classList.add("modal-open");
  });

  if (closeBtn) {
    closeBtn.addEventListener("click", () => {
      modal.classList.remove("open");
      document.body.classList.remove("modal-open");
    });
  }

  modal.addEventListener("click", (event) => {
    if (event.target === modal) {
      modal.classList.remove("open");
      document.body.classList.remove("modal-open");
    }
  });

  if (saveBtn) {
    saveBtn.addEventListener("click", () => {
      modal.classList.remove("open");
      document.body.classList.remove("modal-open");
    });
  }
}

function renderProfilePage() {
  renderProfileTags("profileTags");
  renderProfileTags("currentProfileTags");
  renderSavedRestaurants();
  renderVisitHistory();
  setupProfileModal();
}

/* ---------- Wrapped ---------- */
function renderWrappedPage() {
  const wrappedGrid = document.getElementById("wrappedGrid") || document.getElementById("wrappedStats");
  if (!wrappedGrid) return;

  wrappedGrid.innerHTML = `
    <article class="wrap-card">
      <strong>Top cuisine</strong>
      <p>Chinese</p>
    </article>
    <article class="wrap-card">
      <strong>Most visited area</strong>
      <p>Chinatown</p>
    </article>
    <article class="wrap-card">
      <strong>Most consistent vibe</strong>
      <p>Quiet</p>
    </article>
    <article class="wrap-card">
      <strong>New cuisines tried</strong>
      <p>3</p>
    </article>
  `;
}

/* ---------- Page router ---------- */
function initPage() {
  bindHamburger();
  bindGlobalButtons();
  renderFooterYear();

  const page = document.body.dataset.page;

  if (page === "home") renderHomePage();
  if (page === "discover") renderDiscoverPage();
  if (page === "profile") renderProfilePage();
  if (page === "wrapped") renderWrappedPage();
}

document.addEventListener("DOMContentLoaded", initPage);
