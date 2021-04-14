<template>
  <div class="container-fluid">
    <div class="row" id="search">
      <div class="my-auto col-lg-4 offset-lg-4 col-md-8 offset-md-2 text-start">
        <label for="keywords" class="fs-2 fw-bold text-light"
          >前往特定股票的各站傳送門。</label
        >
        <div class="input-group">
          <input
            type="text"
            class="form-control form-control-lg"
            name="keywords"
            id="keywords"
            placeholder="請輸入代號"
            aria-describedby="keywordsTip"
            autocomplete="off"
            v-model="keyword"
          />
          <button type="button" class="btn btn-primary">
            <i class="bi-search"></i>
          </button>
        </div>
        <div id="keywordsTip" class="form-text text-light">
          範例: <span class="text-warning">2330, </span><span class="text-warning text-decoration-line-through">台積電, 台GG, TSMC</span>
        </div>
        <!-- datalists -->
      </div>
    </div>
  </div>
  <div class="container-xl">
    <div class="fw-bold fs-6 mt-4 mb-1">傳送門</div>
    <div class="row gy-4">
      <div
        class="card-group col-4 g-4"
        v-for="site in sitelist"
        :key="site.name"
      >
        <div class="card">
          <div class="card-body d-flex flex-column">
            <h5 class="card-title">{{ site.name }}</h5>
            <p class="card-text flex-fill">
              <span v-for="tag in site.tags" :key="site.name + tag" class="ms-2"
                >#{{ tag }}</span
              >
            </p>
            <div class="align-self-end">
              <a
                :href="site.url.replace(/%s/, keyword)"
                class="btn btn-primary"
                target="_blank"
                >前往{{ keyword }}</a
              >
            </div>
          </div>
        </div>
      </div>
      <hr class="mt-4" />
      <div class="fw-bold fs-6 mt-2 mb-1">PTT企業綽號列表</div>
      <iframe class="mt-0" src="https://pttpedia.fandom.com/zh/wiki/PTT%E4%BC%81%E6%A5%AD%E7%B6%BD%E8%99%9F%E5%88%97%E8%A1%A8" height="1000"></iframe>
    </div>
  </div>
</template>

<script>
export default {
  name: "Portal",
  data() {
    return {
      keyword: "",
      sitelist: [
        {
          name: "HiStock嗨投資",
          url: "https://histock.tw/stock/%s",
          tags: ["布林通道", "行事曆"],
        },
        {
          name: "玩股網",
          url: "https://www.wantgoo.com/stock/%s",
          tags: ["布林通道", "進階會員功能"],
        },
        {
          name: "Goodinfo!台股資訊網",
          url:
            "https://goodinfo.tw/StockInfo/EquityDistributionCatHis.asp?STOCK_ID=%s",
          tags: [],
        },
        {
          name: "Fugle玉山富果",
          url: "https://www.fugle.tw/ai/%s",
          tags: ["PTT", "自訂資訊卡", "即時筆記", "股票比較", "進階會員功能"],
        },
        { name: "Google", url: "https://www.google.com/search?q=%s", tags: [] },
      ],
    };
  },
};
</script>

<style>
#search {
  background-image: url("../assets/stock-2.jpg");
  background-color: cornflowerblue;
  height: 40vh;
  background-size: cover;
}
</style>