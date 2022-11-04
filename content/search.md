+++
title = "Search"
+++

<div class="hs-demo container" x-data="searchController" id="search-main" style="
    min-height: 410px;">
    <div class="row mt-5">
      <div class="col-6">
        <div class="hs-container">
          <div class="input-group input-group-lg mb-5">
            <input
              type="search"
              x-model="query"
              @click="search()"
              class="form-control"
              aria-label="Large"
              aria-describedby="inputGroup-sizing-sm"
              placeholder="Search ..." />
          </div>
          <div
            x-transition.opacity
            x-show="result.hits.length > 0"
            class="hs-result-inner">
            <template x-for="item in result.hits" :key="item.objectID">
              <ul class="lgrp">
                <li>
                 <!--  <img :src="item.image" /> -->
                  <h4 x-text="item.categories"></h4>
                  <a :href="item.permalink" target="_blank"><h5 class="card-title" x-text="item.post_title"></h5></a>
                  <small x-text="item.author_name"></small>
                  <hr/>
                </li>
              </ul>
            </template>                       
          </div>
        </div>
      </div>
      <div class="col" id="search-facet">
        <ul class="list-group">
          <template x-for="g in result.genre" :key="g.k">
            <li class="list-group-item">
              <span x-text="g.k"></span>
              <span class="badge rounded-pill bg-info" x-text="g.v"></span>
            </li>
          </template>
        </ul>
      </div>
    </div>
  </div>
