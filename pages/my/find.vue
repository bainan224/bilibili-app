
 <template>
  <div class="wrapper">
    <ul>
        <li>
            <img src="../../static/image/find/1.png" alt="">
            <span>兴趣圈</span>
        </li>
        <li>
            <img src="../../static/image/find/2.png" alt="">
            <span>话题中心</span>
        <li>
            <img src="../../static/image/find/1.png" alt="">
            <span>活动中心</span>
        </li>
    </ul>
    <ul>
        <li>
            <img src="../../static/image/find/2.png" alt="">
            <span>原创排行榜</span>
        </li>
        <li>
            <img src="../../static/image/find/1.png" alt="">
            <span>全区排行榜</span>
        </li>

    </ul>
    <ul>
        <li>
            <img src="../../static/image/find/2.png" alt="">
            <span>游戏中心</span>
        </li>
        <li>
            <img src="../../static/image/find/1.png" alt="">
            <span>周边商城</span>
        </li>

    </ul>
  </div>
</template>

<script>
export default {
    data () {
        return {
            
        }
    }
}
</script>

<style lang="scss" scoped>
ul {
    padding-top: 1rem;
}
li {
    width: 100%;
    height: 3.5rem;
    background-color: #FAFAFA;
    border-bottom: 1px solid #EAEAEA;
    display: flex;
    align-items: center;
    img {
        vertical-align: center;
    }
}
</style>
