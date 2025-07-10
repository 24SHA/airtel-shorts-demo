import streamlit as st
import random

st.set_page_config(page_title="Airtel Shorts Recommender", layout="centered")

# ---- Title ----
st.title("📽️ Airtel Xstream Play: Shorts Recommender Demo")
st.markdown("---")

# ---- Persona Selection ----
persona = st.selectbox("Choose your user persona:", [
    "Binge Watcher", "Snack Consumer", "Explorer", "Passive Viewer"])

st.markdown(f"### 🎯 Current Persona: `{persona}`")
st.markdown("---")

# ---- Shorts Database ----
shorts_db = {
    "Action": ["⚡ Fight Scene", "🚗 Car Chase", "🔥 Explosion Clip"],
    "Comedy": ["🤣 Stand-up Snippet", "😂 Sitcom Scene", "😜 Funny Skit"],
    "Drama": ["💔 Emotional Scene", "😢 Tearjerker Moment", "🎭 Monologue"],
    "Sports": ["🏏 Cricket Highlight", "⚽ Goal Clip", "🏀 Slam Dunk"]
}

# ---- Persona to Genre Mapping ----
persona_map = {
    "Binge Watcher": ["Drama", "Action"],
    "Snack Consumer": ["Comedy", "Sports"],
    "Explorer": ["Drama", "Comedy", "Action", "Sports"],
    "Passive Viewer": ["Comedy"]
}

# ---- Session State Setup ----
if "likes" not in st.session_state:
    st.session_state.likes = []
if "skips" not in st.session_state:
    st.session_state.skips = []
if "conversions" not in st.session_state:
    st.session_state.conversions = []

# ---- Recommendation Feed ----
st.subheader("🎬 Recommended Shorts")
genres = persona_map[persona]
for genre in genres:
    short = random.choice(shorts_db[genre])
    with st.container():
        st.markdown(f"**{short}**  _({genre})_")
        col1, col2, col3 = st.columns(3)
        with col1:
            if st.button(f"▶️ Watch Full - {short}", key=f"watch_{short}"):
                st.success(f"You chose to watch the full {genre} content!")
                st.session_state.conversions.append(short)
        with col2:
            if st.button(f"👎 Skip - {short}", key=f"skip_{short}"):
                st.info(f"{short} skipped.")
                st.session_state.skips.append(short)
        with col3:
            if st.button(f"❤️ Like - {short}", key=f"like_{short}"):
                st.success(f"{short} liked. We'll show more like this!")
                st.session_state.likes.append(short)

# ---- Feedback Summary ----
st.markdown("---")
st.subheader("🔁 Feedback Summary")
col1, col2, col3 = st.columns(3)
with col1:
    st.metric("Liked Shorts", len(st.session_state.likes))
with col2:
    st.metric("Watched Full", len(st.session_state.conversions))
with col3:
    st.metric("Skipped Shorts", len(st.session_state.skips))

if st.session_state.likes:
    st.markdown("**Top Liked Shorts:**")
    st.write(st.session_state.likes)

if st.session_state.conversions:
    st.markdown("**Converted to Long-form:**")
    st.write(st.session_state.conversions)

if st.session_state.skips:
    st.markdown("**Skipped Shorts:**")
    st.write(st.session_state.skips)

st.markdown("---")
st.caption("This is a demo simulation for APM interview purposes. No real content used.")
