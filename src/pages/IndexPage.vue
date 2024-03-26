<template>
  <div class="content">
    <div v-for="(video, index) in videos" :key="index" class="video-card">
      <q-img :src="video.thumbnail" :alt="video.title" class="content-img" />
      <div class="video-info">
        <q-avatar class="uploader-avatar" size="sm">
          <img :src="video.uploaderAvatar" alt="Uploader Avatar" />
        </q-avatar>
        <div class="info-text">
          <p class="video-title">{{ video.title }}</p>
          <p class="uploader-name">Uploaded by {{ video.uploader }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      videos: [
        {
          title: "Video 1",
          thumbnail: "https://cdn.quasar.dev/img/parallax1.jpg",
          uploader: "User 1",
          uploaderAvatar: "https://via.placeholder.com/40",
        },
        {
          title: "Video 2",
          thumbnail: "https://cdn.quasar.dev/img/parallax2.jpg",
          uploader: "User 2",
          uploaderAvatar: "https://via.placeholder.com/40",
        },
        {
          title: "Video 3",
          thumbnail: "https://cdn.quasar.dev/img/mountains.jpg",
          uploader: "User 3",
          uploaderAvatar: "https://via.placeholder.com/40",
        },
        {
          title: "Video 4",
          thumbnail: "https://cdn.quasar.dev/img/quasar.jpg",
          uploader: "User 4",
          uploaderAvatar: "https://via.placeholder.com/40",
        },
      ],
    };
  },
};
</script>

<style scoped>
.content {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  margin-top: 1rem;
}

.video-card {
  width: calc(50% - 10px);
  margin-bottom: 20px;
}

.content-img {
  width: 100%;
  height: 300px;
  border-radius: 8px;
}

.video-info {
  display: flex;
  align-items: center;
  margin-top: 10px;
}

.uploader-avatar {
  margin-right: 10px;
}

.video-title {
  font-weight: bold;
  margin-bottom: 5px;
}

.uploader-name {
  color: #888;
  font-size: 0.9rem;
}
</style>
