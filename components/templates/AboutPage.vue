<template>
<div class="about">
<section id="box01">
  <div class="common-box">
    <TitSection
      titleTag="h3"
      titleClass="serif"
      titleText="Since 1999."
      class="tit-section"
    />
    <p class="txt">その時そのときでやりたいことが異なって。<br>
    その度にこのウェブサイトも形を変えているわけですが、名前だけはずっといまのまま。</p>
    <p class="txt serif">cafe NORTH FOXES</p>
  </div>
</section><!--/box01-->

<section id="box02">
  <div class="common-box">
    <TitSection
      titleTag="h3"
      titleClass="serif"
      titleText="About me."
      class="tit-section"
    />
    <p class="txt">主に海外のミステリ・SF・ファンタジィを中心に読書する翻訳小説読み。時々帰国。<br>
    自分でも自分好みの話を書きますが最近はぱったりおとなしく。いつの間にか、"reading better than writing"。でもこれじゃいかんよな、と。</p>
    <p class="txt">だってまわりのみんなは年間200～300冊読むのにこちとら100冊が精一杯。「読書が趣味」なんて迂闊に言えない時代で、「読むことが書くことより好き」なんてどの口が言うんだというわけです。</p>
  </div>
</section><!--/box02-->

<section id="box03">
  <div class="common-box">
    <TitSection
      titleTag="h3"
      titleClass="serif"
      titleText="I want to dance again."
      class="tit-section"
    />
    <p class="txt">当面は、気に入った本の一言感想をほそぼそと。</p>
  </div>
</section><!--/box03-->
</div>
</template>

<script>
import TitSection from '@/components/atoms/TitSection.vue'

export default{
  components: {
    TitSection
  },
  head() {
    return {
      title: 'About｜cafe NORTHFOXES',
    }
  },
}
</script>

<style lang="scss" scoped>
#box01{
  padding-top: per(60,$tab);
}
</style>