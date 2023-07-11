<template>
    <div>
        <h1>Trang ảnh</h1>
        <!-- Hiển thị danh sách ảnh đã tải -->
        <div v-if="photos.length > 0">
            <h2>Các ảnh đã tải:</h2>
            <ul>
                <li v-for="photo in photos" :key="photo.id">
                    <img :src="photo.url" alt="Ảnh">
                </li>
            </ul>
        </div>
        <!-- Form tải ảnh -->
        <div>
            <h2>Tải ảnh:</h2>
            <input type="file" @change="uploadPhoto">
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            photos: [] // Danh sách ảnh đã tải
        }
    },
    methods: {
        uploadPhoto(event) {
            // Xử lý logic tải ảnh lên server
            const file = event.target.files[0]
            // Gửi file lên server, nhận lại thông tin ảnh đã tải thành công
            // Sau khi tải thành công, thêm thông tin ảnh vào danh sách this.photos
        }
    }
}
</script>
