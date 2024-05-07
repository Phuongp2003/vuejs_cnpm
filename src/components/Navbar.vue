<template>
    <nav class="navbar navbar-expand-lg bg-body-tertiary" data-bs-theme="dark">
        <div class="container-fluid">
            <a class="navbar-brand" href="#">075PhamBuiNamPhuong</a>
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse"
                data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false"
                aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarSupportedContent">
                <ul class="navbar-nav me-auto mb-2 mb-lg-0">
                    <li class="nav-item">
                        <a class="nav-link active" aria-current="page" href="#">Trang chủ</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="https://github.com/Phuongp2003">Thông tin</a>
                    </li>
                    <li class="nav-item dropdown">
                        <a class="nav-link dropdown-toggle" href="#" role="button" data-bs-toggle="dropdown"
                            aria-expanded="false">
                            Các sản phẩm
                        </a>
                        <ul class="dropdown-menu">
                            <li><a class="dropdown-item" href="https://github.com/Phuongp2003/MyGodotProject">Game</a>
                            </li>
                            <li><a class="dropdown-item" href="https://github.com/Phuongp2003/LTWeb_PTITHCM">Web</a>
                            </li>
                            <li><a class="dropdown-item" href="https://github.com/Phuongp2003/CTDL_N7">Đồ án</a></li>
                        </ul>
                    </li>
                </ul>
            </div>
        </div>
    </nav>
</template>

<style scooped>
.nav-item,
li {
    margin-bottom: 0px;
}
</style>

<script>
export default {
    name: 'Navbar'
}
</script>
