<script lang="ts">
  import { onMount, onDestroy } from 'svelte';

  export let baseText = "BiblAI helps you";
  export let dynamicTexts = [
    "learn scripture",
    "practice faith",
    "discover God's word",
    "grow spiritually",
    "study the Bible",
    "reflect on verses",
    "deepen your faith",
    "explore biblical wisdom",
    "connect with God",
    "understand theology",
    "apply biblical principles",
    "meditate on scripture",
    "find spiritual guidance",
    "strengthen your beliefs",
    "engage with the Bible",
    "gain biblical insights",
    "develop Christian habits",
    "nurture your soul",
    "experience God's love",
    "live out your faith",
    "embrace divine teachings",
    "cultivate spiritual disciplines",
    "uncover biblical truths",
    "walk with Jesus",
    "transform your life"
  ];

  let currentText = "";
  let currentIndex = 0;
  let isDeleting = false;
  let typingSpeed = 100;
  let deletingSpeed = 50;
  let pauseDuration = 2000;

  let timeoutId: number;

  function typeText() {
    const fullText = dynamicTexts[currentIndex];
    
    if (!isDeleting && currentText === fullText) {
      isDeleting = true;
      timeoutId = setTimeout(typeText, pauseDuration);
      return;
    }

    if (isDeleting && currentText === "") {
      isDeleting = false;
      currentIndex = (currentIndex + 1) % dynamicTexts.length;
      timeoutId = setTimeout(typeText, typingSpeed);
      return;
    }

    const nextText = isDeleting
      ? fullText.substring(0, currentText.length - 1)
      : fullText.substring(0, currentText.length + 1);
    
    currentText = nextText;

    timeoutId = setTimeout(typeText, isDeleting ? deletingSpeed : typingSpeed);
  }

  onMount(() => {
    typeText();
  });

  onDestroy(() => {
    clearTimeout(timeoutId);
  });
</script>

<h1 class="h2 dynamic-title">
  {baseText} <span class="dynamic-text">{currentText}</span>
</h1>

<style>
  .dynamic-title {
  }

  .dynamic-text {
    color: #0066cc;
    border-right: 2px solid #0066cc;
    padding-right: 5px;
    animation: blink-caret 0.75s step-end infinite;
  }

  @keyframes blink-caret {
    from, to { border-color: transparent }
    50% { border-color: #0066cc; }
  }
</style>
