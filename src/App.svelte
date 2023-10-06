<script>
  import { onMount } from "svelte";

  import DiceBoard from "./DiceBoard.svelte";

  onMount(() => {
    document.getElementById("sprite-svg").addEventListener("load", function() {
      const svg = this.getSVGDocument().rootElement;
      svg.id = "sprite-svg";
      this.parentNode.replaceChild(svg, this);
    }, {once: true });
  })
</script>

<div class="page-wrapper"><img src="assets/images/decor/desktop-corner@2x.png" class="page-corner --top-left" /> <img src="assets/images/decor/desktop-corner@2x.png" class="page-corner --top-right" /> <img src="assets/images/decor/desktop-corner@2x.png" class="page-corner --bottom-left" /> <img src="assets/images/decor/desktop-corner@2x.png" class="page-corner --bottom-right" />
  <div class="wallets mode-garden">
      <div class="header-actions">
          <div class="price-label --medium --yellow mode-garden"><svg class="icon-svg icon-svg_gp price-label__icon">
                  <use xlink:href="#gp"></use>
              </svg>
              <div class="price-label__text">
                  <div class="price-label__text-value">77999 GP <span class="price-label__text-icon"></span></div>
                  <div class="price-label__sub">
                      <div class="chance-label">x28 Chance</div>
                      <div class="text-xxs text-up fw-b ff-acsent color-acsent">GP Bonus</div>
                  </div>
              </div>
          </div>
          <div class="price-label --medium mode-garden"><svg class="icon-svg icon-svg_agt price-label__icon">
                  <use xlink:href="#agt"></use>
              </svg>
              <div class="price-label__text">
                  <div class="price-label__text-value">799 AGT <span class="price-label__text-icon"></span></div>
              </div>
          </div>
          <div class="btn-wrapper"><button class="btn btn-hover --decor-side --warning --decor btn-account" style="" data-toggler-id="modalAccountResponsive" data-toggler-desktop-id="modalAccountResponsive"><span class="btn-decor"></span> <span class="btn-decor-side --small"></span> <span class="btn-title --small text-grad grad-yellow-down"><span>Connect Wallet</span></span></button></div>
      </div>
  </div>
  <header class="header mode-garden">
      <div class="container">
          <div class="header__inner">
              <div class="header__toggle mr-a"><button type="button" class="btn-menu" data-toggler-id="modalMenuResponsive" data-toggler-desktop-id="modalMenuResponsive"><img src="/assets/images/burger.svg" alt="" /></button></div>
          </div>
          <div class="header__content">
              <div class="chat-panel-container mode-garden">
                  <div class="chat-panel__bg-curves"><img src="assets/images/garden/garden-header-bg.png" srcset="assets/images/garden/garden-header-bg.png, assets/images/garden/garden-header-bg@2x.png 2x" class="chat-panel__bg-curves__center" /> <img src="assets/images/garden/garden-header-decor.png" srcset="assets/images/garden/garden-header-decor.png, assets/images/garden/garden-header-decor@2x.png 2x" class="chat-panel__bg-curves__wing --left" /> <img src="assets/images/garden/garden-header-decor@2x.png" srcset="assets/images/garden/garden-header-decor.png, assets/images/garden/garden-header-decor@2x.png 2x" class="chat-panel__bg-curves__wing --right" /></div>
                  <div class="chat-panel-wrapper">
                      <div class="chat-panel"><img src="assets/images/chat/panel-round.svg" alt="treasure">
                          <div class="chat-panel__content"><img src="assets/images/logo-small.png" srcset="assets/images/logo-small.png, assets/images/logo-small@2x.png 2x" alt="Sultan">
                              <div class="chat-panel__treasure ff-text text-up fw-b text-xxs text-grad grad-yellow-down">Treasury</div>
                              <div class="ff-main text-small text-grad grad-yellow-down">1 157 029</div>
                              <div class="chat-panel__value ff-acsent text-small fw-b text-grad grad-yellow-down">BNB</div>
                          </div>
                      </div>
                      <div class="chat-panel__progress">
                          <div class="chat-panel-progress" onclick="(new ChatPage()).progress(8)"><img src="assets/images/chat/progress-bg.svg" class="chat-progress-bg" />
                              <div class="chat-progress-dots chat-progress-dots--progress-7"><img src="assets/images/chat/progress-dot-1.svg" class="chat-progress-dot" /><img src="assets/images/chat/progress-dot-1.svg" class="chat-progress-dot" /><img src="assets/images/chat/progress-dot-1.svg" class="chat-progress-dot" /><img src="assets/images/chat/progress-dot-1.svg" class="chat-progress-dot" /><img src="assets/images/chat/progress-dot-2.svg" class="chat-progress-dot" /><img src="assets/images/chat/progress-dot-2.svg" class="chat-progress-dot" /><img src="assets/images/chat/progress-dot-2.svg" class="chat-progress-dot" /><img src="assets/images/chat/progress-dot-2.svg" class="chat-progress-dot" /><img src="assets/images/chat/progress-dot-3.svg" class="chat-progress-dot" /><img src="assets/images/chat/progress-dot-3.svg" class="chat-progress-dot" /><img src="assets/images/chat/progress-dot-3.svg" class="chat-progress-dot" /><img src="assets/images/chat/progress-dot-3.svg" class="chat-progress-dot" /></div>
                              <div class="chat-panel-progress__text ff-acsent text-up fw-b text-xxs">Progress: <span>7</span>/12</div>
                          </div>
                      </div>
                      <div class="chat-panel__left">
                          <div class="chat-panel-info"><img src="assets/images/chat/panel-info.svg" alt="Soon">
                              <div class="chat-panel-info__content ff-acsent fw-b text-xxs text-grad grad-yellow-down chat-panel-info__content--soon">× × × × × × ×</div>
                              <div class="chat-panel-info__text ff-acsent fw-b text-xxs">Soon</div>
                          </div>
                      </div>
                      <div class="chat-panel__right">
                          <div class="chat-panel-info"><img src="assets/images/chat/panel-info.svg" alt="Time Left">
                              <div class="chat-panel-info__content ff-acsent fw-b text-xxs text-grad grad-yellow-down chat-panel-info__content--timer">23h 49m 17s</div>
                              <div class="chat-panel-info__text ff-acsent fw-b text-xxs">Time Left</div>
                          </div>
                      </div>
                  </div>
              </div>
          </div>
          <div class="header__title">
              <div class="action-title">
                  <div class="action-title__txt"><span class="text-grad grad-yellow-down">Sultan’s Gardens</span></div>
                  <div class="action-title__decore"><img src="assets/images/garden/action-title-back-layer.png" srcset="assets/images/garden/action-title-back-layer.png, assets/images/garden/action-title-back-layer@2x.png 2x" class="action-title__back-layer" /> <img src="assets/images/garden/action-title-layer.png" srcset="assets/images/garden/action-title-layer.png, assets/images/garden/action-title-layer@2x.png 2x" class="action-title__layer" /></div>
              </div>
          </div>
      </div>
  </header>
  <main class="page-content page-garden" style="background-image: url(assets/images/gareden-bg.jpg);">
      <div class="hero"><img class="hero__img" src="assets/images/garden/ape.png" srcset="assets/images/garden/ape.png, assets/images/garden/ape@2x.png 2x" alt="ape" /></div>
      <div class="container">
          <div class="dialog">
              <div class="dialog__view">
                  <div class="dialog__speach" data-toggler-id="modalAlert" data-toggler-desktop-id="modalAlert">Ты выходишь в сад и видишь совершенно ничем не занятого обезъяна. Обезъян крутит на пальце ключи от винного погреба</div>
              </div>
              <div class="dialog__action"><button class="btn btn-hover --decor btn-action" data-toggler-id="modalHeroAction" data-toggler-desktop-id="modalHeroAction"><span class="btn-decor"></span>
                      <div class="btn-title d-flex ai-c jc-sb"><span class="btn-action-txt text-grad grad-yellow_light">Take the keys</span> <span class="d-flex ai-c as-fe"><span class="btn-action-descr">Difficulty</span> <span class="btn-action-media"><span class="btn-action-media__txt text-grad grad-yellow_light">14</span></span></span></div>
                  </button></div>
              <div class="dialog__action"><button class="btn btn-hover --decor --success btn-action" data-toggler-id="modalHeroDialog" data-toggler-desktop-id="modalHeroDialog"><span class="btn-decor"></span>
                      <div class="btn-title d-flex ai-c jc-sb"><span class="btn-action-txt text-grad grad-yellow_light">Ask Ape for help Ask Ape for help Ask Ape for help Ask Ape for help </span><span class="d-flex ai-c as-fe"><span class="btn-action-descr">Chat with AI-Ape</span> <span class="btn-action-media"><span class="btn-action-media__txt text-grad grad-yellow_light">:-)</span></span></span></div>
                  </button></div>
          </div>
      </div>
  </main>
  <script>
      document.addEventListener("DOMContentLoaded", () => {
          window.IndexHeroes();
      }, false);
  </script>
  <div id="modalHeroAction" class="modal modal-center modal-heroAction" data-position="center" data-touch="false">
      <div class="modal-blur"></div>
      <div class="modal-backdrop" data-toggler-id="modalHeroAction">
        <img src="assets/images/decor/desktop-corner@2x.png" 
        class="page-corner --top-left" /> 
        <img src="assets/images/decor/desktop-corner@2x.png" 
        class="page-corner --top-right" /> 
        <img src="assets/images/decor/desktop-corner@2x.png" 
        class="page-corner --bottom-left" /> 
        <img src="assets/images/decor/desktop-corner@2x.png" 
        class="page-corner --bottom-right" />
      </div>
      <div class="modal-head">
          <div class="container --relative d-flex ai-fs jc-c">
              <div class="modal__close"><button class="btn btn-close" data-toggler-id="modalHeroAction"><img src="assets/images/close.svg" alt="close" /></button></div>
              <div class="modal__title">
                  <div class="action-title">
                      <div class="action-title__txt"><span class="text-grad grad-yellow-down">Sultan’s Gardens</span></div>
                      <div class="action-title__decore"><img src="assets/images/garden/action-title-back-layer.png" srcset="assets/images/garden/action-title-back-layer.png, assets/images/garden/action-title-back-layer@2x.png 2x" class="action-title__back-layer" /> <img src="assets/images/garden/action-title-layer.png" srcset="assets/images/garden/action-title-layer.png, assets/images/garden/action-title-layer@2x.png 2x" class="action-title__layer" /></div>
                      <div class="action-title__number"><span class="ff-acsent fw-b text-grad grad-yellow-down">14</span></div>
                      <div class="action-title__descr"><span class="text-small ff-acsent fw-b text-grad grad-yellow-down">Difficulty</span></div>
                  </div>
              </div>
          </div>
      </div>
      <div class="modal-body">
          <div class="modal-bg-container">
              <div class="hero-actions">
                  <div class="hero-actions__random">
                      <div class="action-random">
                          <div class="action-random__board relative">
                            
                            <div class="absolute inset-0 z-[51] w-full aspect-square sm:aspect-auto">
                              <DiceBoard />
                            </div>

                            <!-- <img src="assets/images/garden/dice.png" alt="dice" />  -->

                            
                            <img 
                              src="assets/images/garden/action-corner.png" 
                              srcset="assets/images/garden/action-corner.png, assets/images/garden/action-corner@2x.png 2x" 
                              class="page-corner action-corner --top-left --medium --default" 
                            /> 
                            <img 
                              src="assets/images/garden/action-corner_error.png" 
                              srcset="assets/images/garden/action-corner_error.png, assets/images/garden/action-corner_error@2x.png 2x" 
                              class="page-corner action-corner --top-left --medium --failed" 
                            /> 
                            <span class="page-corner --top-left action-corner action-corner_text ff-text">Отнять ключи у Обезъяна</span> 
                            <img 
                              src="assets/images/garden/action-corner.png" 
                              srcset="assets/images/garden/action-corner.png, assets/images/garden/action-corner@2x.png 2x" 
                              class="page-corner action-corner --bottom-right --medium --default" 
                            /> 
                            <img 
                              src="assets/images/garden/action-corner_error.png" 
                              srcset="assets/images/garden/action-corner_error.png, assets/images/garden/action-corner_error@2x.png 2x" 
                              class="page-corner action-corner --bottom-right --medium --failed" 
                            /> <span class="page-corner --bottom-right action-corner action-corner_text ff-text">Обезъян отдает тебе ключи и недовольно урчит</span>
                              <div class="action-random__randomizer">
                                  <div class="action-random__dice"><span class="action-random__txt action-random__txt_before fw-b text-grad grad-yellow-down">EPIC</span> <span class="action-random__txt action-random__txt_before fw-b text-grad grad-error">EPIC</span> 
                                  <span class="action-random__txt action-random__txt_after fw-b text-grad grad-yellow-down">WIN</span> 
                                  <span class="action-random__txt action-random__txt_after fw-b text-grad grad-error">FAIL</span></div>
                              </div>
                          </div>
                      </div>
                  </div>
                  <div class="hero-actions__nav">
                      <div class="hero-actions__nav_start">
                          <div class="action-nav action-nav_start">
                            <button class="btn btn-hover --increased --decor --badge js-demo-start opacity-0">
                              <span class="btn-decor"></span> 
                              <span class="btn-title --up text-grad grad-yellow-down">
                                Roll the dice
                              </span> 
                            <span class="btn-badge"><span class="badge"><span class="badge__txt">
                                              <div class="price-label --yellow"><svg class="icon-svg icon-svg_gp price-label__icon">
                                                      <use xlink:href="#gp"></use>
                                                  </svg>
                                                  <div class="price-label__text">
                                                      <div class="price-label__text__value">77999 GP</div>
                                                  </div>
                                              </div>
                                          </span></span></span>
                          </button>
                        </div>
                      </div>
                      <div class="hero-actions__nav_win">
                          <div class="action-nav action-nav_win">
                              <div class="text-xl text-grad grad-yellow-down text-up fw-b">Progress: 7/12</div>
                              <div class="text-xl color-acsent text-up fw-b">+700 GP</div><button class="btn btn-hover --increased --decor js-demo-win"><span class="btn-decor"></span> <span class="btn-title --up text-grad grad-yellow-down">Continue</span></button>
                          </div>
                      </div>
                      <div class="hero-actions__nav_win-process">
                          <div class="action-nav action-nav_win-process">
                              <div class="text-xl text-grad grad-yellow-down text-up fw-b">Progress: 7/12</div>
                              <div class="text-xl color-acsent text-up fw-b">+700 GP</div><button class="btn btn-hover --increased --decor js-demo-continue"><span class="btn-decor"></span> <span class="btn-title --up text-grad grad-yellow-down">Continue</span></button>
                          </div>
                      </div>
                      <div class="hero-actions__nav_lose">
                          <div class="action-nav action-nav_lose"><button class="btn btn-hover --increased --decor --badge js-demo-reroll"><span class="btn-decor"></span> <span class="btn-title --up text-grad grad-yellow-down">Reroll</span> <span class="btn-badge"><span class="badge"><span class="badge__txt">
                                              <div class="price-label --yellow"><svg class="icon-svg icon-svg_gp price-label__icon">
                                                      <use xlink:href="#gp"></use>
                                                  </svg>
                                                  <div class="price-label__text">
                                                      <div class="price-label__text__value">77999 GP</div>
                                                  </div>
                                              </div>
                                          </span></span></span></button></div>
                      </div>
                  </div>
                  <div class="hero-actions__tools">
                      <div class="action-tools">
                          <div class="action-tools__panel">
                              <div class="action-tools__itm">
                                  <div class="action-tool ff-acsent">
                                      <div class="action-tool__img"><img class="action-tool__main-img" src="assets/images/garden/lasso.png" srcset="assets/images/garden/lasso.png, assets/images/garden/lasso@2x.png 2x" alt="Lasso" /></div>
                                      <div class="action-tool__title fw-b">Lasso<div class="action-tool__check"><img class="action-tool__check-img" src="assets/images/garden/check.svg" alt="v" /></div>
                                      </div>
                                      <div class="action-tool__descr">
                                          <div class="action-tool__descr-content"><span class="fw-b text-grad grad-acsent-up">Bonus: +4</span></div>
                                      </div>
                                      <div class="action-tool__info action-tool__info_price"><span class="action-tool__info-content">
                                              <div class="price-label --yellow"><svg class="icon-svg icon-svg_gp price-label__icon">
                                                      <use xlink:href="#gp"></use>
                                                  </svg>
                                                  <div class="price-label__text">
                                                      <div class="price-label__text__value">321 GP</div>
                                                  </div>
                                              </div>
                                          </span></div>
                                  </div>
                              </div>
                              <div class="action-tools__itm">
                                  <div class="action-tool ff-acsent checked">
                                      <div class="action-tool__img"><img class="action-tool__main-img" src="assets/images/garden/ladder.png" srcset="assets/images/garden/ladder.png, assets/images/garden/ladder@2x.png 2x" alt="Ladder" /></div>
                                      <div class="action-tool__title fw-b">Ladder<div class="action-tool__check"><img class="action-tool__check-img" src="assets/images/garden/check.svg" alt="v" /></div>
                                      </div>
                                      <div class="action-tool__descr">
                                          <div class="action-tool__descr-content"><span class="fw-b text-grad grad-acsent-up">Bonus: +12</span></div>
                                      </div>
                                      <div class="action-tool__info action-tool__info_price"><span class="action-tool__info-content">
                                              <div class="price-label --yellow"><svg class="icon-svg icon-svg_gp price-label__icon">
                                                      <use xlink:href="#gp"></use>
                                                  </svg>
                                                  <div class="price-label__text">
                                                      <div class="price-label__text__value">321 GP</div>
                                                  </div>
                                              </div>
                                          </span></div>
                                      <div class="action-tool__badge"><img class="action-tool__badge-img" src="assets/images/garden/ape-ava.png" srcset="assets/images/garden/ape-ava.png, assets/images/garden/ape-ava@2x.png 2x" alt="ape" /></div>
                                  </div>
                              </div>
                              <div class="action-tools__itm">
                                  <div class="action-tool ff-acsent">
                                      <div class="action-tool__img"><img class="action-tool__main-img" src="assets/images/garden/stone.png" srcset="assets/images/garden/stone.png, assets/images/garden/stone@2x.png 2x" alt="Stone" /></div>
                                      <div class="action-tool__title fw-b">Stone<div class="action-tool__check"><img class="action-tool__check-img" src="assets/images/garden/check.svg" alt="v" /></div>
                                      </div>
                                      <div class="action-tool__descr">
                                          <div class="action-tool__descr-content"><span class="fw-b text-grad grad-acsent-up">Bonus: +8</span></div>
                                      </div>
                                      <div class="action-tool__info action-tool__info_txt"><span class="action-tool__info-content fw-b text-grad grad-yellow-down text-up">Get From AI</span></div>
                                      <div class="action-tool__badge"><img class="action-tool__badge-img" src="assets/images/garden/ape-ava.png" srcset="assets/images/garden/ape-ava.png, assets/images/garden/ape-ava@2x.png 2x" alt="ape" /></div>
                                  </div>
                              </div>
                              <div class="action-tools__itm">
                                  <div class="action-tool ff-acsent checked debuff">
                                      <div class="action-tool__img"><img class="action-tool__main-img" src="assets/images/garden/skull.png" srcset="assets/images/garden/skull.png, assets/images/garden/skull@2x.png 2x" alt="lasso" /></div>
                                      <div class="action-tool__title fw-b">Penalty<div class="action-tool__check"><img class="action-tool__check-img" src="assets/images/garden/check.svg" alt="v" /></div>
                                      </div>
                                      <div class="action-tool__descr">
                                          <div class="action-tool__descr-content"><span class="fw-b text-grad grad-acsent-up grad-error">Bonus: -12</span></div>
                                      </div>
                                      <div class="action-tool__info action-tool__info_price"><span class="action-tool__info-content">
                                              <div class="price-label --yellow"><svg class="icon-svg icon-svg_gp price-label__icon">
                                                      <use xlink:href="#gp"></use>
                                                  </svg>
                                                  <div class="price-label__text">
                                                      <div class="price-label__text__value">321 GP</div>
                                                  </div>
                                              </div>
                                          </span></div>
                                      <div class="action-tool__badge"><img class="action-tool__badge-img" src="assets/images/garden/ape-ava.png" srcset="assets/images/garden/ape-ava.png, assets/images/garden/ape-ava@2x.png 2x" alt="ape" /></div>
                                  </div>
                              </div>
                              <div class="action-tools__itm">
                                  <div class="action-tool ff-acsent">
                                      <div class="action-tool__img"><img class="action-tool__main-img" src="assets/images/garden/lasso.png" srcset="assets/images/garden/lasso.png, assets/images/garden/lasso@2x.png 2x" alt="lasso" /></div>
                                      <div class="action-tool__title fw-b">Lasso<div class="action-tool__check"><img class="action-tool__check-img" src="assets/images/garden/check.svg" alt="v" /></div>
                                      </div>
                                      <div class="action-tool__descr">
                                          <div class="action-tool__descr-content"><span class="fw-b text-grad grad-acsent-up">Bonus: +4</span></div>
                                      </div>
                                      <div class="action-tool__info action-tool__info_price"><span class="action-tool__info-content">
                                              <div class="price-label --yellow"><svg class="icon-svg icon-svg_gp price-label__icon">
                                                      <use xlink:href="#gp"></use>
                                                  </svg>
                                                  <div class="price-label__text">
                                                      <div class="price-label__text__value">321 GP</div>
                                                  </div>
                                              </div>
                                          </span></div>
                                  </div>
                              </div>
                          </div>
                          <div class="action-tools__txt"><span class="text-grad grad-yellow-down text-up fw-b">Total Bonuses:</span> <span class="badge"><span class="badge__txt text-grad grad-yellow-down text-up fw-b">12</span></span></div>
                      </div>
                  </div>
              </div>
          </div>
      </div>
  </div>
  <div id="modalHeroDialog" class="modal modal-center modal-heroAction" data-position="center" data-touch="false">
      <div class="modal-blur"></div>
      <div class="modal-backdrop" data-toggler-id="modalHeroDialog"><img src="assets/images/decor/desktop-corner@2x.png" class="page-corner --top-left" /> <img src="assets/images/decor/desktop-corner@2x.png" class="page-corner --top-right" /> <img src="assets/images/decor/desktop-corner@2x.png" class="page-corner --bottom-left" /> <img src="assets/images/decor/desktop-corner@2x.png" class="page-corner --bottom-right" /></div>
      <div class="modal-head">
          <div class="container --relative d-flex ai-fs jc-c">
              <div class="modal__close"><button class="btn btn-close" data-toggler-id="modalCloseDialog"><img src="assets/images/close.svg" alt="close" /></button></div>
              <div class="modal__title">
                  <div class="action-title">
                      <div class="action-title__txt"><span class="text-grad grad-yellow-down">Sultan’s Gardens</span></div>
                      <div class="action-title__decore"><img src="assets/images/garden/action-title-back-layer.png" srcset="assets/images/garden/action-title-back-layer.png, assets/images/garden/action-title-back-layer@2x.png 2x" class="action-title__back-layer" /> <img src="assets/images/garden/action-title-layer.png" srcset="assets/images/garden/action-title-layer.png, assets/images/garden/action-title-layer@2x.png 2x" class="action-title__layer" /></div>
                  </div>
              </div>
          </div>
      </div>
      <div class="modal-body">
          <div class="modal-bg-container">
              <div class="hero-dialog">
                  <div class="action-progress">
                      <div class="action-progress__side --left"><img src="assets/images/garden/coin.png" srcset="assets/images/garden/coin.png, assets/images/garden/coin@2x.png 2x" class="action-progress__side-img" /></div>
                      <div class="action-progress__itm --first">
                          <div class="action-progress__itm-img"><img src="assets/images/garden/face_angry.png" srcset="assets/images/garden/face_angry.png, assets/images/garden/face_angry@2x.png 2x" class="img" /></div>
                          <div class="action-progress__itm-dot"><img src="assets/images/chat/progress-dot-1.svg" class="img" /></div>
                      </div>
                      <div class="action-progress__itm">
                          <div class="action-progress__itm-img"><img src="assets/images/garden/face_diagonal.png" srcset="assets/images/garden/face_diagonal.png, assets/images/garden/face_diagonal@2x.png 2x" class="img" /></div>
                          <div class="action-progress__itm-dot"><img src="assets/images/chat/progress-dot-1.svg" class="img" /></div>
                      </div>
                      <div class="action-progress__hero"><img src="assets/images/garden/ape-waist-high.png" srcset="assets/images/garden/ape-waist-high.png, assets/images/garden/ape-waist-high@2x.png 2x" class="action-progress__hero-img" /> <span class="action-progress__hero-txt fw-b">Bored Ape</span></div>
                      <div class="action-progress__itm --right --active">
                          <div class="action-progress__itm-img"><img src="assets/images/garden/face_raised.png" srcset="assets/images/garden/face_raised.png, assets/images/garden/face_raised@2x.png 2x" class="img" /></div>
                          <div class="action-progress__itm-dot"><img src="assets/images/chat/progress-dot-1.svg" class="img" /></div>
                      </div>
                      <div class="action-progress__itm --right --last">
                          <div class="action-progress__itm-img"><img src="assets/images/garden/face_smile.png" srcset="assets/images/garden/face_smile.png, assets/images/garden/face_smile@2x.png 2x" class="img" /></div>
                          <div class="action-progress__itm-dot"><img src="assets/images/chat/progress-dot-1.svg" class="img" /></div>
                      </div>
                      <div class="action-progress__side --right"><img src="assets/images/garden/box.png" srcset="assets/images/garden/box.png, assets/images/garden/box@2x.png 2x" class="action-progress__side-img" /></div>
                  </div>
                  <div class="action-dialog"><img src="assets/images/garden/action-corner.png" srcset="assets/images/garden/action-corner.png, assets/images/garden/action-corner@2x.png 2x" class="page-corner action-corner --top-left --small --default" /> <img src="assets/images/garden/action-corner_error.png" srcset="assets/images/garden/action-corner_error.png, assets/images/garden/action-corner_error@2x.png 2x" class="page-corner action-corner --top-left --small --failed" /> <img src="assets/images/garden/action-corner.png" srcset="assets/images/garden/action-corner.png, assets/images/garden/action-corner@2x.png 2x" class="page-corner action-corner --bottom-right --small --default" /> <img src="assets/images/garden/action-corner_error.png" srcset="assets/images/garden/action-corner_error.png, assets/images/garden/action-corner_error@2x.png 2x" class="page-corner action-corner --bottom-right --small --failed" />
                      <div class="action-dialog__container">
                          <div class="action-dialog__content">
                              <div class="action-dialog__row">
                                  <div class="speach-bubble">Что же привело тебя в этот прекрасный сад, друг мой?</div>
                              </div>
                              <div class="action-dialog__row">
                                  <div class="speach-bubble --self">Ого! Говорящая обезьяна, в рот мне ноги! Не ешь меня!</div>
                              </div>
                              <div class="action-dialog__row">
                                  <div class="speach-bubble">А знаешь, что...</div>
                              </div>
                              <div class="action-dialog__row">
                                  <div class="speach-bubble">Я ведь не только говорить, я еще и рисовать умею</div>
                              </div>
                              <div class="action-dialog__row">
                                  <div class="speach-bubble">
                                      <div class="typing">
                                          <div class="dot"></div>
                                          <div class="dot"></div>
                                          <div class="dot"></div>
                                      </div>
                                  </div>
                              </div>
                          </div>
                      </div>
                  </div>
                  <div class="dialog-nav">
                      <div class="dialog-nav__row">
                          <div class="dialog-timer"><span class="text-small ff-acsent fw-b text-grad grad-yellow-down">Time Left</span> <span class="badge mx-5"><span class="badge__txt">01:37</span> </span><a href="#" class="text-small ff-acsent fw-b text-grad grad-yellow-down text-underline" data-toggler-id="modalPlayHelpResponsive" data-toggler-desktop-id="modalPlayHelpResponsive">How To Play?</a></div>
                      </div>
                      <div class="dialog-nav__row">
                          <div class="panel panel-answer dialog-answer"><label class="form-input --chat --center"><input class="form-input__field" autocomplete="off" name="message" placeholder="Try to convince Bored Ape by typing anything..." value=""></label>
                              <div class="panel-answer__action"><svg class="icon-svg icon-svg_send">
                                      <use xlink:href="#send"></use>
                                  </svg></div>
                          </div>
                      </div>
                      <div class="dialog-nav__row"><span class="ff-acsent fw-b text-grad grad-yellow-down">Dialog with Bored Ape AI</span></div>
                  </div>
              </div>
          </div>
      </div>
  </div>
  <div id="modalAlert" class="modal modal-center" data-position="center" data-touch="false">
      <div class="modal-blur"></div>
      <div class="modal-backdrop" data-toggler-id="modalAlert"></div>
      <div class="modal-body">
          <div class="alert"><img src="assets/images/garden/alert-layer.png" srcset="assets/images/garden/alert-layer.png, assets/images/garden/alert-layer@2x.png 2x" class="alert__bg" />
              <div class="alert__row"><img class="alert__img ml-a mr-a" src="assets/images/garden/alert-triangle.svg" alt="!" />
                  <div class="alert__title fw-b text-grad grad-yellow-down">Not enough GP <svg class="icon-svg icon-svg_gp alert__txt-icon">
                          <use xlink:href="#gp"></use>
                      </svg></div>
              </div>
              <div class="alert__row">
                  <div class="fw-sb mb-10">You need more GP to roll the dice. You can buy more GP or convert AGP and BNB to GP</div><button class="btn btn-hover --success --decor --increased" style="" data-toggler-id="modalAlert"><span class="btn-decor"></span> <span class="btn-title --up text-grad grad-yellow-down"><span>BUY GP</span></span></button>
              </div>
              <div class="alert__row">
                  <div class="fw-sb mb-10">Convert your other assets to GP <svg class="icon-svg icon-svg_gp alert__txt-icon">
                          <use xlink:href="#gp"></use>
                      </svg></div>
                  <div class="d-flex ai-c jc-c gap-10 fw-w"><button class="btn btn-hover --success --decor btn-small" style="" data-toggler-id="modalAlert"><span class="btn-decor"></span> <span class="btn-title --up text-grad grad-yellow-down"><span>AGT → GP</span></span></button> <button class="btn btn-hover --decor btn-small" style="" data-toggler-id="modalAlert"><span class="btn-decor"></span> <span class="btn-title --up text-grad grad-yellow-down"><span>BNB → GP</span></span></button> <button class="btn btn-hover --decor btn-small" style="" data-toggler-id="modalAlert"><span class="btn-decor"></span> <span class="btn-title --up text-grad grad-yellow-down"><span>GET BNB</span></span></button></div>
              </div>
              <div class="alert__row"><a href="#" class="fw-b text-up text-underline" data-toggler-id="modalAlert">NO, THANKS</a></div>
          </div>
      </div>
  </div>
  <div id="modalPlayHelpResponsive" class="modal modal-bottom modal-main" data-position="bottom">
      <div class="modal-head">
          <div class="container --relative">
              <div class="modal__close"><button class="btn btn-close" data-toggler-id="modalPlayHelpResponsive"><img src="assets/images/close.svg" alt="close" /></button></div>
          </div>
      </div>
      <div class="modal-backdrop" data-toggler-id="modalPlayHelpResponsive"></div>
      <div class="modal-body --bottom">
          <div class="container --fh">
              <div class="modal-bg-container --bottom"><svg class="modal-bg --big --desktop" preserveAspectRatio="none" viewBox="15 0 800 800" fill="none" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
                      <path d="M15 160C15 93.7258 68.7258 40 135 40H263.369C284.102 40 304.404 34.4568 323.249 25.8119C348.322 14.3101 385.454 0 415 0C444.546 0 481.678 14.3101 506.751 25.8119C525.596 34.4568 545.898 40 566.631 40H695C761.274 40 815 93.7258 815 160V800H15V160Z" fill="url(#paint0_linear_453_24788)" />
                      <g filter="url(#filter0_d_453_24788)">
                          <mask id="mask0_453_24788" style="mask-type:alpha" maskUnits="userSpaceOnUse" x="775" y="66" width="51" height="83">
                              <rect x="775" y="142.581" width="77.3333" height="40" transform="rotate(-82 775 142.581)" fill="url(#pattern0)" />
                          </mask>
                          <g mask="url(#mask0_453_24788)">
                              <rect x="785.695" y="66.4795" width="40" height="77.3333" transform="rotate(8 785.695 66.4795)" fill="url(#paint1_linear_453_24788)" />
                          </g>
                      </g>
                      <g filter="url(#filter1_d_453_24788)">
                          <mask id="mask1_453_24788" style="mask-type:alpha" maskUnits="userSpaceOnUse" x="4" y="66" width="51" height="83">
                              <rect width="77.3333" height="40" transform="matrix(-0.139173 -0.990268 -0.990268 0.139173 54.3735 142.581)" fill="url(#pattern1)" />
                          </mask>
                          <g mask="url(#mask1_453_24788)">
                              <rect width="40" height="77.3333" transform="matrix(-0.990268 0.139173 0.139173 0.990268 43.6782 66.4795)" fill="url(#paint2_linear_453_24788)" />
                          </g>
                      </g>
                      <defs>
                          <filter id="filter0_d_453_24788" x="763" y="54" width="66.3735" height="98.1484" filterUnits="userSpaceOnUse" color-interpolation-filters="sRGB">
                              <feFlood flood-opacity="0" result="BackgroundImageFix" />
                              <feColorMatrix in="SourceAlpha" type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 127 0" result="hardAlpha" />
                              <feOffset dx="-4" dy="-4" />
                              <feGaussianBlur stdDeviation="4" />
                              <feComposite in2="hardAlpha" operator="out" />
                              <feColorMatrix type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0.5 0" />
                              <feBlend mode="normal" in2="BackgroundImageFix" result="effect1_dropShadow_453_24788" />
                              <feBlend mode="normal" in="SourceGraphic" in2="effect1_dropShadow_453_24788" result="shape" />
                          </filter>
                          <pattern id="pattern0" patternContentUnits="objectBoundingBox" width="1" height="1">
                              <use xlink:href="#image0_453_24788" transform="matrix(0.00261233 0 0 0.00505051 -0.00548588 0)" />
                          </pattern>
                          <filter id="filter1_d_453_24788" x="0" y="54" width="66.3735" height="98.1484" filterUnits="userSpaceOnUse" color-interpolation-filters="sRGB">
                              <feFlood flood-opacity="0" result="BackgroundImageFix" />
                              <feColorMatrix in="SourceAlpha" type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 127 0" result="hardAlpha" />
                              <feOffset dx="4" dy="-4" />
                              <feGaussianBlur stdDeviation="4" />
                              <feComposite in2="hardAlpha" operator="out" />
                              <feColorMatrix type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0.5 0" />
                              <feBlend mode="normal" in2="BackgroundImageFix" result="effect1_dropShadow_453_24788" />
                              <feBlend mode="normal" in="SourceGraphic" in2="effect1_dropShadow_453_24788" result="shape" />
                          </filter>
                          <pattern id="pattern1" patternContentUnits="objectBoundingBox" width="1" height="1">
                              <use xlink:href="#image0_453_24788" transform="matrix(0.00261233 0 0 0.00505051 -0.00548588 0)" />
                          </pattern>
                          <linearGradient id="paint0_linear_453_24788" x1="415" y1="0" x2="415" y2="800" gradientUnits="userSpaceOnUse">
                              <stop stop-color="#171717" />
                              <stop offset="1" />
                          </linearGradient>
                          <linearGradient id="paint1_linear_453_24788" x1="805.695" y1="66.4795" x2="805.695" y2="143.813" gradientUnits="userSpaceOnUse">
                              <stop stop-color="#F0AB00" />
                              <stop offset="0.46875" stop-color="#E63801" />
                              <stop offset="1" stop-color="#0F0F0F" />
                          </linearGradient>
                          <linearGradient id="paint2_linear_453_24788" x1="20" y1="0" x2="20" y2="77.3333" gradientUnits="userSpaceOnUse">
                              <stop stop-color="#F0AB00" />
                              <stop offset="0.46875" stop-color="#E63801" />
                              <stop offset="1" stop-color="#0F0F0F" />
                          </linearGradient>
                          <image id="image0_453_24788" width="387" height="198" xlink:href="assets/images/modals/modal_decor.png" />
                      </defs>
                  </svg>
                  <div class="modal-bg-content-scroll px-30 custom-scroll">
                      <div class="help-content content-center">
                          <div class="text-center">
                              <div class="logo-brand _light"><img src="assets/images/logo-parrot.png" srcset="assets/images/logo-parrot.png, assets/images/logo-parrot@2x.png 2x" class="logo-brand__bird" alt="parrot" width="28" height="56" /> <img width="235" class="logo-brand__img" height="108" src="assets/images/logo.svg" alt="Sultan" />
                                  <p class="logo-brand-title">First AI Web 3.0 Game</p>
                              </div>
                          </div>
                          <div class="divider my-10"><svg width="160" height="16" viewBox="0 0 160 16" fill="none" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
                                  <mask id="mask0_3205_305" style="mask-type:alpha" maskUnits="userSpaceOnUse" x="0" y="0" width="160" height="16">
                                      <rect width="160" height="15.0978" fill="url(#patternDivider)" />
                                  </mask>
                                  <g mask="url(#mask0_3205_305)">
                                      <rect width="160" height="15.1" fill="url(#paint0_linear_3205_305)" />
                                  </g>
                                  <defs>
                                      <pattern id="patternDivider" patternContentUnits="objectBoundingBox" width="1" height="1">
                                          <use xlink:href="#image12_3205_305" transform="scale(0.000283366 0.003003)" />
                                      </pattern>
                                      <linearGradient id="paint0_linear_3205_305" x1="80.9195" y1="-1.42004e-07" x2="80.9195" y2="15.1" gradientUnits="userSpaceOnUse">
                                          <stop stop-color="#E63801" />
                                          <stop offset="1" stop-color="#FCE361" />
                                      </linearGradient>
                                      <image id="image12_3205_305" width="3529" height="333" xlink:href="assets/images/modals/modal_divider.png" />
                                  </defs>
                              </svg></div>
                          <ul class="list-num text-left">
                              <li>
                                  <p>Al Sultan speaks to you, responding to your remarks and emotions.</p>
                              </li>
                              <li>
                                  <p>You have an Al Assistant, who for ACGT game tokens gives hints on how best to convince Al Sultan to sequentially open 12 doors of the treasury.</p>
                              </li>
                              <li>
                                  <p>You can ask any clarifying questions and make assumptions to increase your chances of success and change the cost of hints.</p>
                              </li>
                              <li>
                                  <p>Convince the Sultan and claim your reward in BNB!</p>
                              </li>
                              <li>
                                  <p>You can get anything from a small share to the entire HUGE treasury of Al Sultan!</p>
                              </li>
                              <li>
                                  <p>Acquire AGT: the more tokens you have in your balance, the higher the chance to claim the ENTIRE Treasury!</p>
                              </li>
                              <li>
                                  <p>Hurry up! Al Sultan is ready to chat only until midnight, after which all the treasury doors opened today will close, and all AGT tokens on your balance will burn.</p>
                              </li>
                              <li>
                                  <p>However, each day, the generous Assistant will give you 2000 AGT for free, so you can compete for the treasury again!</p>
                              </li>
                              <li>
                                  <p>If you bring a friend you'll get another 1000!</p>
                              </li>
                          </ul>
                      </div>
                  </div>
              </div>
          </div>
      </div>
  </div>
  <div id="modalCloseDialog" data-position="center" data-modal-index="1002" class="modal modal-center modal-responsive">
      <div class="modal-blur"></div>
      <div class="modal-backdrop" data-toggler-id="modalCloseDialog"></div>
      <div class="modal-body --center --medium --overflow-visible">
          <div class="container px-0">
              <div class="modal-bg-container --center --overflow-visible"><svg preserveaspectratio="none" class="modal-bg --desktop-s --offset" width="510" height="440" viewBox="0 0 510 440" fill="none" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
                      <path d="M15 120C15 75.8172 50.8172 40 95 40H144.62C164.191 40 182.905 32.5058 199.242 21.728C215.22 11.1865 236.528 0 255 0C273.472 0 294.78 11.1865 310.758 21.728C327.095 32.5058 345.809 40 365.38 40H415C459.183 40 495 75.8172 495 120V320C495 364.183 459.183 400 415 400H365.38C345.809 400 327.095 407.494 310.758 418.272C294.78 428.813 273.472 440 255 440C236.528 440 215.22 428.813 199.242 418.272C182.905 407.494 164.191 400 144.62 400H95C50.8172 400 15 364.183 15 320V120Z" fill="url(#paint0_linear_453_24772)" />
                      <g filter="url(#filter0_d_453_24772)">
                          <mask id="mask0_453_24772" style="mask-type:alpha" maskUnits="userSpaceOnUse" x="454" y="40" width="52" height="83">
                              <rect x="454.997" y="116.581" width="77.3333" height="40" transform="rotate(-82 454.997 116.581)" fill="url(#pattern0)" />
                          </mask>
                          <g mask="url(#mask0_453_24772)">
                              <rect x="465.693" y="40.4795" width="40" height="77.3333" transform="rotate(8 465.693 40.4795)" fill="url(#paint1_linear_453_24772)" />
                          </g>
                      </g>
                      <g filter="url(#filter1_d_453_24772)">
                          <mask id="mask1_453_24772" style="mask-type:alpha" maskUnits="userSpaceOnUse" x="4" y="40" width="51" height="83">
                              <rect width="77.3333" height="40" transform="matrix(-0.139173 -0.990268 -0.990268 0.139173 54.3735 116.581)" fill="url(#pattern1)" />
                          </mask>
                          <g mask="url(#mask1_453_24772)">
                              <rect width="40" height="77.3333" transform="matrix(-0.990268 0.139173 0.139173 0.990268 43.6782 40.4795)" fill="url(#paint2_linear_453_24772)" />
                          </g>
                      </g>
                      <g filter="url(#filter2_d_453_24772)">
                          <mask id="mask2_453_24772" style="mask-type:alpha" maskUnits="userSpaceOnUse" x="454" y="317" width="52" height="83">
                              <rect width="77.3333" height="40" transform="matrix(0.139173 0.990268 0.990268 -0.139173 454.997 323.419)" fill="url(#pattern2)" />
                          </mask>
                          <g mask="url(#mask2_453_24772)">
                              <rect width="40" height="77.3333" transform="matrix(0.990268 -0.139173 -0.139173 -0.990268 465.693 399.521)" fill="url(#paint3_linear_453_24772)" />
                          </g>
                      </g>
                      <g filter="url(#filter3_d_453_24772)">
                          <mask id="mask3_453_24772" style="mask-type:alpha" maskUnits="userSpaceOnUse" x="4" y="317" width="51" height="83">
                              <rect x="54.3735" y="323.419" width="77.3333" height="40" transform="rotate(98 54.3735 323.419)" fill="url(#pattern3)" />
                          </mask>
                          <g mask="url(#mask3_453_24772)">
                              <rect x="43.6782" y="399.521" width="40" height="77.3333" transform="rotate(-172 43.6782 399.521)" fill="url(#paint4_linear_453_24772)" />
                          </g>
                      </g>
                      <defs>
                          <filter id="filter0_d_453_24772" x="442.997" y="28" width="66.3734" height="98.1484" filterUnits="userSpaceOnUse" color-interpolation-filters="sRGB">
                              <feFlood flood-opacity="0" result="BackgroundImageFix" />
                              <feColorMatrix in="SourceAlpha" type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 127 0" result="hardAlpha" />
                              <feOffset dx="-4" dy="-4" />
                              <feGaussianBlur stdDeviation="4" />
                              <feComposite in2="hardAlpha" operator="out" />
                              <feColorMatrix type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0.5 0" />
                              <feBlend mode="normal" in2="BackgroundImageFix" result="effect1_dropShadow_453_24772" />
                              <feBlend mode="normal" in="SourceGraphic" in2="effect1_dropShadow_453_24772" result="shape" />
                          </filter>
                          <pattern id="pattern0" patternContentUnits="objectBoundingBox" width="1" height="1">
                              <use xlink:href="#image0_453_24772" transform="matrix(0.00261233 0 0 0.00505051 -0.00548588 0)" />
                          </pattern>
                          <filter id="filter1_d_453_24772" x="0" y="28" width="66.3735" height="98.1484" filterUnits="userSpaceOnUse" color-interpolation-filters="sRGB">
                              <feFlood flood-opacity="0" result="BackgroundImageFix" />
                              <feColorMatrix in="SourceAlpha" type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 127 0" result="hardAlpha" />
                              <feOffset dx="4" dy="-4" />
                              <feGaussianBlur stdDeviation="4" />
                              <feComposite in2="hardAlpha" operator="out" />
                              <feColorMatrix type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0.5 0" />
                              <feBlend mode="normal" in2="BackgroundImageFix" result="effect1_dropShadow_453_24772" />
                              <feBlend mode="normal" in="SourceGraphic" in2="effect1_dropShadow_453_24772" result="shape" />
                          </filter>
                          <pattern id="pattern1" patternContentUnits="objectBoundingBox" width="1" height="1">
                              <use xlink:href="#image0_453_24772" transform="matrix(0.00261233 0 0 0.00505051 -0.00548588 0)" />
                          </pattern>
                          <filter id="filter2_d_453_24772" x="442.997" y="313.852" width="66.3734" height="98.1484" filterUnits="userSpaceOnUse" color-interpolation-filters="sRGB">
                              <feFlood flood-opacity="0" result="BackgroundImageFix" />
                              <feColorMatrix in="SourceAlpha" type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 127 0" result="hardAlpha" />
                              <feOffset dx="-4" dy="4" />
                              <feGaussianBlur stdDeviation="4" />
                              <feComposite in2="hardAlpha" operator="out" />
                              <feColorMatrix type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0.5 0" />
                              <feBlend mode="normal" in2="BackgroundImageFix" result="effect1_dropShadow_453_24772" />
                              <feBlend mode="normal" in="SourceGraphic" in2="effect1_dropShadow_453_24772" result="shape" />
                          </filter>
                          <pattern id="pattern2" patternContentUnits="objectBoundingBox" width="1" height="1">
                              <use xlink:href="#image0_453_24772" transform="matrix(0.00261233 0 0 0.00505051 -0.00548588 0)" />
                          </pattern>
                          <filter id="filter3_d_453_24772" x="0" y="313.852" width="66.3735" height="98.1484" filterUnits="userSpaceOnUse" color-interpolation-filters="sRGB">
                              <feFlood flood-opacity="0" result="BackgroundImageFix" />
                              <feColorMatrix in="SourceAlpha" type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 127 0" result="hardAlpha" />
                              <feOffset dx="4" dy="4" />
                              <feGaussianBlur stdDeviation="4" />
                              <feComposite in2="hardAlpha" operator="out" />
                              <feColorMatrix type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0.5 0" />
                              <feBlend mode="normal" in2="BackgroundImageFix" result="effect1_dropShadow_453_24772" />
                              <feBlend mode="normal" in="SourceGraphic" in2="effect1_dropShadow_453_24772" result="shape" />
                          </filter>
                          <pattern id="pattern3" patternContentUnits="objectBoundingBox" width="1" height="1">
                              <use xlink:href="#image0_453_24772" transform="matrix(0.00261233 0 0 0.00505051 -0.00548588 0)" />
                          </pattern>
                          <linearGradient id="paint0_linear_453_24772" x1="255" y1="0" x2="255" y2="440" gradientUnits="userSpaceOnUse">
                              <stop stop-color="#171717" />
                              <stop offset="1" />
                          </linearGradient>
                          <linearGradient id="paint1_linear_453_24772" x1="485.693" y1="40.4795" x2="485.693" y2="117.813" gradientUnits="userSpaceOnUse">
                              <stop stop-color="#F0AB00" />
                              <stop offset="0.46875" stop-color="#E63801" />
                              <stop offset="1" stop-color="#0F0F0F" />
                          </linearGradient>
                          <linearGradient id="paint2_linear_453_24772" x1="20" y1="0" x2="20" y2="77.3333" gradientUnits="userSpaceOnUse">
                              <stop stop-color="#F0AB00" />
                              <stop offset="0.46875" stop-color="#E63801" />
                              <stop offset="1" stop-color="#0F0F0F" />
                          </linearGradient>
                          <linearGradient id="paint3_linear_453_24772" x1="20" y1="0" x2="20" y2="77.3333" gradientUnits="userSpaceOnUse">
                              <stop stop-color="#F0AB00" />
                              <stop offset="0.46875" stop-color="#E63801" />
                              <stop offset="1" stop-color="#0F0F0F" />
                          </linearGradient>
                          <linearGradient id="paint4_linear_453_24772" x1="63.6782" y1="399.521" x2="63.6782" y2="476.854" gradientUnits="userSpaceOnUse">
                              <stop stop-color="#F0AB00" />
                              <stop offset="0.46875" stop-color="#E63801" />
                              <stop offset="1" stop-color="#0F0F0F" />
                          </linearGradient>
                          <image id="image0_453_24772" width="387" height="198" xlink:href="assets/images/modals/modal_decor.png" />
                      </defs>
                  </svg>
                  <div class="modal-head-icon modal-head-icon_hero"><img class="" src="assets/images/garden/ape.png" srcset="assets/images/garden/ape.png, assets/images/garden/ape@2x.png 2x" alt="ape" /></div>
                  <div class="modal-bg-content --center">
                      <div class="closeDialog-content">
                          <div class="text-center px-40 mb-30">If you close the dialog with the Bored Api AI now, next try will cost you <span class="fw-b color-acsent whitespace-nowrap">3000 GP</span></div>
                          <div class="text-center mb-30"><button class="btn btn-hover --decor --increased" style="" data-toggler-id="modalHeroDialog"><span class="btn-decor"></span> <span class="btn-title --up text-grad grad-yellow-down"><span>Close Dialog</span></span></button></div>
                          <div class="text-center"><button class="btn btn-hover --success --decor --increased" style="" data-toggler-id="modalCloseDialog"><span class="btn-decor"></span> <span class="btn-title --up text-grad grad-yellow-down"><span>Continue chatting</span></span></button></div>
                      </div>
                  </div>
              </div>
          </div>
      </div>
  </div>
  <div id="modalMenuResponsive" class="modal modal-bottom modal-main" data-position="bottom">
      <div class="modal-head --visible-right">
          <div class="container">
              <div class="modal__close"><button class="btn btn-close" data-toggler-id="modalMenuResponsive"><img src="assets/images/close.svg" alt="close" /></button> <button class="btn btn-back" data-toggler-id=""><img src="assets/images/back.svg" alt="back" /></button></div>
          </div>
      </div>
      <div class="modal-backdrop" data-toggler-id="modalMenuResponsive"></div>
      <div class="modal-body --bottom">
          <div class="modal-bg-container --bottom"><svg class="modal-bg --big --desktop mobile-hidden" preserveAspectRatio="none" viewBox="15 0 800 800" fill="none" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
                  <path d="M15 160C15 93.7258 68.7258 40 135 40H263.369C284.102 40 304.404 34.4568 323.249 25.8119C348.322 14.3101 385.454 0 415 0C444.546 0 481.678 14.3101 506.751 25.8119C525.596 34.4568 545.898 40 566.631 40H695C761.274 40 815 93.7258 815 160V800H15V160Z" fill="url(#paint0_linear_453_24788)" />
                  <g filter="url(#filter0_d_453_24788)">
                      <mask id="mask0_453_24788" style="mask-type:alpha" maskUnits="userSpaceOnUse" x="775" y="66" width="51" height="83">
                          <rect x="775" y="142.581" width="77.3333" height="40" transform="rotate(-82 775 142.581)" fill="url(#pattern0)" />
                      </mask>
                      <g mask="url(#mask0_453_24788)">
                          <rect x="785.695" y="66.4795" width="40" height="77.3333" transform="rotate(8 785.695 66.4795)" fill="url(#paint1_linear_453_24788)" />
                      </g>
                  </g>
                  <g filter="url(#filter1_d_453_24788)">
                      <mask id="mask1_453_24788" style="mask-type:alpha" maskUnits="userSpaceOnUse" x="4" y="66" width="51" height="83">
                          <rect width="77.3333" height="40" transform="matrix(-0.139173 -0.990268 -0.990268 0.139173 54.3735 142.581)" fill="url(#pattern1)" />
                      </mask>
                      <g mask="url(#mask1_453_24788)">
                          <rect width="40" height="77.3333" transform="matrix(-0.990268 0.139173 0.139173 0.990268 43.6782 66.4795)" fill="url(#paint2_linear_453_24788)" />
                      </g>
                  </g>
                  <defs>
                      <filter id="filter0_d_453_24788" x="763" y="54" width="66.3735" height="98.1484" filterUnits="userSpaceOnUse" color-interpolation-filters="sRGB">
                          <feFlood flood-opacity="0" result="BackgroundImageFix" />
                          <feColorMatrix in="SourceAlpha" type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 127 0" result="hardAlpha" />
                          <feOffset dx="-4" dy="-4" />
                          <feGaussianBlur stdDeviation="4" />
                          <feComposite in2="hardAlpha" operator="out" />
                          <feColorMatrix type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0.5 0" />
                          <feBlend mode="normal" in2="BackgroundImageFix" result="effect1_dropShadow_453_24788" />
                          <feBlend mode="normal" in="SourceGraphic" in2="effect1_dropShadow_453_24788" result="shape" />
                      </filter>
                      <pattern id="pattern0" patternContentUnits="objectBoundingBox" width="1" height="1">
                          <use xlink:href="#image0_453_24788" transform="matrix(0.00261233 0 0 0.00505051 -0.00548588 0)" />
                      </pattern>
                      <filter id="filter1_d_453_24788" x="0" y="54" width="66.3735" height="98.1484" filterUnits="userSpaceOnUse" color-interpolation-filters="sRGB">
                          <feFlood flood-opacity="0" result="BackgroundImageFix" />
                          <feColorMatrix in="SourceAlpha" type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 127 0" result="hardAlpha" />
                          <feOffset dx="4" dy="-4" />
                          <feGaussianBlur stdDeviation="4" />
                          <feComposite in2="hardAlpha" operator="out" />
                          <feColorMatrix type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0.5 0" />
                          <feBlend mode="normal" in2="BackgroundImageFix" result="effect1_dropShadow_453_24788" />
                          <feBlend mode="normal" in="SourceGraphic" in2="effect1_dropShadow_453_24788" result="shape" />
                      </filter>
                      <pattern id="pattern1" patternContentUnits="objectBoundingBox" width="1" height="1">
                          <use xlink:href="#image0_453_24788" transform="matrix(0.00261233 0 0 0.00505051 -0.00548588 0)" />
                      </pattern>
                      <linearGradient id="paint0_linear_453_24788" x1="415" y1="0" x2="415" y2="800" gradientUnits="userSpaceOnUse">
                          <stop stop-color="#171717" />
                          <stop offset="1" />
                      </linearGradient>
                      <linearGradient id="paint1_linear_453_24788" x1="805.695" y1="66.4795" x2="805.695" y2="143.813" gradientUnits="userSpaceOnUse">
                          <stop stop-color="#F0AB00" />
                          <stop offset="0.46875" stop-color="#E63801" />
                          <stop offset="1" stop-color="#0F0F0F" />
                      </linearGradient>
                      <linearGradient id="paint2_linear_453_24788" x1="20" y1="0" x2="20" y2="77.3333" gradientUnits="userSpaceOnUse">
                          <stop stop-color="#F0AB00" />
                          <stop offset="0.46875" stop-color="#E63801" />
                          <stop offset="1" stop-color="#0F0F0F" />
                      </linearGradient>
                      <image id="image0_453_24788" width="387" height="198" xlink:href="assets/images/modals/modal_decor.png" />
                  </defs>
              </svg>
              <div class="menu-full">
                  <div class="menu-full__decor-corner"></div>
                  <div class="menu-full__logo"><img src="assets/images/logo-medium.png" alt="Sultan"></div>
                  <div class="mobile-hidden">
                      <div class="menu-full-head"><button class="btn btn-hover --decor active" style=""><span class="btn-decor"></span> <span class="btn-title --up text-grad grad-yellow-down"><svg class="icon-svg icon-svg_menu btn-title-icon">
                                      <use xlink:href="#menu"></use>
                                  </svg> <span>Menu</span></span></button> <button class="btn btn-hover --decor" style=""><span class="btn-decor"></span> <span class="btn-title --up text-grad grad-yellow-down"><svg class="icon-svg icon-svg_market btn-title-icon">
                                      <use xlink:href="#market"></use>
                                  </svg> <span>Market</span></span></button> <button class="btn btn-hover --decor" style=""><span class="btn-decor"></span> <span class="btn-title --up text-grad grad-yellow-down"><svg class="icon-svg icon-svg_rating btn-title-icon">
                                      <use xlink:href="#rating"></use>
                                  </svg> <span>Rating</span></span></button> <button class="btn btn-hover --decor" style=""><span class="btn-decor"></span> <img src="assets/images/buttons/referral@2x.png" alt="Referral program" /> <span class="btn-title --up --small text-grad grad-yellow-down"><svg class="icon-svg icon-svg_referral btn-title-icon">
                                      <use xlink:href="#referral"></use>
                                  </svg> <span>Referral<br />program</span></span></button></div>
                  </div>
                  <div class="divider-light mt-20 mb-10 mobile-hidden"></div>
                  <div class="menu-full-body --visible-right">
                      <div class="menu-full-body__left custom-scroll">
                          <div class="menu-container" id="contentMenu">
                              <div class="header-menu menu-main">
                                  <div class="header-menu__inner">
                                      <div class="header-nav">
                                          <div class="divider-title">Game</div>
                                          <ul class="header-nav__list">
                                              <li class="header-nav__item"><a class="header-nav__link">Golden Market<div class="header-nav__link-icon"><svg class="icon-svg icon-svg_chevron-right">
                                                              <use xlink:href="#chevron-right"></use>
                                                          </svg></div></a></li>
                                              <li class="header-nav__item"><a class="header-nav__link active">Settings<div class="header-nav__link-icon"><svg class="icon-svg icon-svg_chevron-right">
                                                              <use xlink:href="#chevron-right"></use>
                                                          </svg></div></a></li>
                                          </ul>
                                      </div>
                                      <div class="header-nav">
                                          <div class="divider-title">Support</div>
                                          <ul class="header-nav__list">
                                              <li class="header-nav__item"><a class="header-nav__link">Discord <span class="header-nav__link-count">23 793</span>
                                                      <div class="header-nav__link-icon"><svg class="icon-svg icon-svg_s icon-svg_s-link-out">
                                                              <use xlink:href="#s-link-out"></use>
                                                          </svg></div>
                                                  </a></li>
                                              <li class="header-nav__item"><a class="header-nav__link">FAQ<div class="header-nav__link-icon"><svg class="icon-svg icon-svg_chevron-right">
                                                              <use xlink:href="#chevron-right"></use>
                                                          </svg></div></a></li>
                                              <li class="header-nav__item"><a class="header-nav__link">Support<div class="header-nav__link-icon"><svg class="icon-svg icon-svg_chevron-right">
                                                              <use xlink:href="#chevron-right"></use>
                                                          </svg></div></a></li>
                                          </ul>
                                      </div>
                                      <div class="header-nav">
                                          <div class="divider-title">Legal</div>
                                          <ul class="header-nav__list">
                                              <li class="header-nav__item"><a class="header-nav__link --link">Privacy Policy</a></li>
                                              <li class="header-nav__item"><a class="header-nav__link --link">Terms of Use</a></li>
                                          </ul>
                                      </div>
                                  </div>
                              </div>
                          </div>
                      </div>
                      <div class="menu-full-body__right custom-scroll">
                          <div class="menu-container" id="contentMenuSettings">
                              <div class="header-menu menu-settings">
                                  <div class="header-menu__inner">
                                      <div class="header-nav">
                                          <div class="divider-title --mb-big">Settings</div>
                                          <ul class="header-nav__list">
                                              <li class="header-nav__item"><label class="header-nav__line header-nav__text"><span>Language </span><select name="language" class="js-select">
                                                          <option>Russian</option>
                                                          <option>English</option>
                                                          <option>German</option>
                                                      </select></label>
                                                  <div class="divider-light mt-30"></div>
                                              </li>
                                          </ul>
                                      </div>
                                  </div>
                              </div>
                          </div>
                      </div>
                  </div>
              </div>
          </div>
      </div>
  </div>
  <div id="modalAccountResponsive" class="modal modal-bottom modal-main" data-position="bottom">
      <div class="modal-blur"></div>
      <div class="modal-backdrop" data-toggler-id="modalAccountResponsive"></div>
      <div class="modal-head">
          <div class="container --relative">
              <div class="modal__close"><button class="btn btn-close" data-toggler-id="modalAccountResponsive"><img src="assets/images/close.svg" alt="close" /></button></div>
          </div>
      </div>
      <div class="modal-body --bottom">
          <div class="modal-bg-container --bottom"><svg class="modal-bg --big --desktop mobile-hidden" preserveAspectRatio="none" viewBox="15 0 800 800" fill="none" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
                  <path d="M15 160C15 93.7258 68.7258 40 135 40H263.369C284.102 40 304.404 34.4568 323.249 25.8119C348.322 14.3101 385.454 0 415 0C444.546 0 481.678 14.3101 506.751 25.8119C525.596 34.4568 545.898 40 566.631 40H695C761.274 40 815 93.7258 815 160V800H15V160Z" fill="url(#paint0_linear_453_24788)" />
                  <g filter="url(#filter0_d_453_24788)">
                      <mask id="mask0_453_24788" style="mask-type:alpha" maskUnits="userSpaceOnUse" x="775" y="66" width="51" height="83">
                          <rect x="775" y="142.581" width="77.3333" height="40" transform="rotate(-82 775 142.581)" fill="url(#pattern0)" />
                      </mask>
                      <g mask="url(#mask0_453_24788)">
                          <rect x="785.695" y="66.4795" width="40" height="77.3333" transform="rotate(8 785.695 66.4795)" fill="url(#paint1_linear_453_24788)" />
                      </g>
                  </g>
                  <g filter="url(#filter1_d_453_24788)">
                      <mask id="mask1_453_24788" style="mask-type:alpha" maskUnits="userSpaceOnUse" x="4" y="66" width="51" height="83">
                          <rect width="77.3333" height="40" transform="matrix(-0.139173 -0.990268 -0.990268 0.139173 54.3735 142.581)" fill="url(#pattern1)" />
                      </mask>
                      <g mask="url(#mask1_453_24788)">
                          <rect width="40" height="77.3333" transform="matrix(-0.990268 0.139173 0.139173 0.990268 43.6782 66.4795)" fill="url(#paint2_linear_453_24788)" />
                      </g>
                  </g>
                  <defs>
                      <filter id="filter0_d_453_24788" x="763" y="54" width="66.3735" height="98.1484" filterUnits="userSpaceOnUse" color-interpolation-filters="sRGB">
                          <feFlood flood-opacity="0" result="BackgroundImageFix" />
                          <feColorMatrix in="SourceAlpha" type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 127 0" result="hardAlpha" />
                          <feOffset dx="-4" dy="-4" />
                          <feGaussianBlur stdDeviation="4" />
                          <feComposite in2="hardAlpha" operator="out" />
                          <feColorMatrix type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0.5 0" />
                          <feBlend mode="normal" in2="BackgroundImageFix" result="effect1_dropShadow_453_24788" />
                          <feBlend mode="normal" in="SourceGraphic" in2="effect1_dropShadow_453_24788" result="shape" />
                      </filter>
                      <pattern id="pattern0" patternContentUnits="objectBoundingBox" width="1" height="1">
                          <use xlink:href="#image0_453_24788" transform="matrix(0.00261233 0 0 0.00505051 -0.00548588 0)" />
                      </pattern>
                      <filter id="filter1_d_453_24788" x="0" y="54" width="66.3735" height="98.1484" filterUnits="userSpaceOnUse" color-interpolation-filters="sRGB">
                          <feFlood flood-opacity="0" result="BackgroundImageFix" />
                          <feColorMatrix in="SourceAlpha" type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 127 0" result="hardAlpha" />
                          <feOffset dx="4" dy="-4" />
                          <feGaussianBlur stdDeviation="4" />
                          <feComposite in2="hardAlpha" operator="out" />
                          <feColorMatrix type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0.5 0" />
                          <feBlend mode="normal" in2="BackgroundImageFix" result="effect1_dropShadow_453_24788" />
                          <feBlend mode="normal" in="SourceGraphic" in2="effect1_dropShadow_453_24788" result="shape" />
                      </filter>
                      <pattern id="pattern1" patternContentUnits="objectBoundingBox" width="1" height="1">
                          <use xlink:href="#image0_453_24788" transform="matrix(0.00261233 0 0 0.00505051 -0.00548588 0)" />
                      </pattern>
                      <linearGradient id="paint0_linear_453_24788" x1="415" y1="0" x2="415" y2="800" gradientUnits="userSpaceOnUse">
                          <stop stop-color="#171717" />
                          <stop offset="1" />
                      </linearGradient>
                      <linearGradient id="paint1_linear_453_24788" x1="805.695" y1="66.4795" x2="805.695" y2="143.813" gradientUnits="userSpaceOnUse">
                          <stop stop-color="#F0AB00" />
                          <stop offset="0.46875" stop-color="#E63801" />
                          <stop offset="1" stop-color="#0F0F0F" />
                      </linearGradient>
                      <linearGradient id="paint2_linear_453_24788" x1="20" y1="0" x2="20" y2="77.3333" gradientUnits="userSpaceOnUse">
                          <stop stop-color="#F0AB00" />
                          <stop offset="0.46875" stop-color="#E63801" />
                          <stop offset="1" stop-color="#0F0F0F" />
                      </linearGradient>
                      <image id="image0_453_24788" width="387" height="198" xlink:href="assets/images/modals/modal_decor.png" />
                  </defs>
              </svg>
              <div class="menu-full">
                  <div class="menu-full__logo mobile-hidden"><img src="assets/images/logo-medium.png" alt="Sultan">
                      <p class="menu-full__logo-id text-grad fw-b grad-yellow-down">Account <span class="text-grad grad-acsent-down">id12578</span></p>
                  </div>
                  <div class="mobile-hidden">
                      <div class="menu-full-head"><button class="btn btn-hover --decor active" style=""><span class="btn-decor"></span> <span class="btn-title --up text-grad grad-yellow-down"><svg class="icon-svg icon-svg_wallet btn-title-icon">
                                      <use xlink:href="#wallet"></use>
                                  </svg> <span>Wallet</span></span></button> <button class="btn btn-hover --decor" style=""><span class="btn-decor"></span> <span class="btn-title --up text-grad grad-yellow-down"><svg class="icon-svg icon-svg_trade btn-title-icon">
                                      <use xlink:href="#trade"></use>
                                  </svg> <span>Trade</span></span></button> <button class="btn btn-hover --decor" style=""><span class="btn-decor"></span> <span class="btn-title --up text-grad grad-yellow-down"><svg class="icon-svg icon-svg_cart btn-title-icon">
                                      <use xlink:href="#cart"></use>
                                  </svg> <span>Buy gp</span></span></button> <button class="btn btn-hover --decor" style=""><span class="btn-decor"></span> <span class="btn-title --up text-grad grad-yellow-down"><svg class="icon-svg icon-svg_market btn-title-icon">
                                      <use xlink:href="#market"></use>
                                  </svg> <span>Market</span></span></button></div>
                  </div>
                  <div class="desktop-hidden px-10">
                      <ul class="tabs">
                          <li class="tabs__item"><button class="tab --active">
                                  <div class="tab__inner">
                                      <div class="tab__title">Balance</div>
                                  </div>
                              </button></li>
                          <li class="tabs__item"><button class="tab">
                                  <div class="tab__inner">
                                      <div class="tab__title">History</div>
                                  </div>
                              </button></li>
                      </ul>
                  </div>
                  <div class="divider-light mt-20 mobile-hidden"></div>
                  <div class="menu-full-body">
                      <div class="menu-full-body__left custom-scroll">
                          <div class="menu-container">
                              <div class="account-balance-content">
                                  <div class="wrapper px-10">
                                      <div class="divider-title --mb-big">Game Wallet</div>
                                      <div class="trade-panel">
                                          <div class="trade-panel__row --panel">
                                              <div class="trade-panel__left">
                                                  <div class="trade-panel-title">Gold Points</div>
                                                  <div class="trade-panel__description color-light">Use GP to play the game. <span class="color-warning">Every night at 12am GMT all GP are burned.</span></div>
                                              </div>
                                              <div class="trade-panel__right"><a class="link-icon --acsent"><span class="link-icon__text">7999 GP </span><span class="link-icon__img"></span></a></div>
                                          </div>
                                          <div class="trade-panel__actions"><button class="btn btn-hover --round-all btn-medium" style=""><span class="btn-title --up text-grad grad-yellow-down"><svg class="icon-svg icon-svg_cart btn-title-icon">
                                                          <use xlink:href="#cart"></use>
                                                      </svg> <span>Buy</span></span></button></div>
                                      </div>
                                      <div class="trade-panel">
                                          <div class="trade-panel__row --panel">
                                              <div class="trade-panel__left">
                                                  <div class="trade-panel-title">Uncollected AGT prizes</div>
                                                  <div class="trade-panel__description color-light">Save exceeding Gold Points by exchanging them to AGT.</div>
                                              </div>
                                              <div class="trade-panel__right"><a class="link-icon"><span class="link-icon__text acsent">799 AGT </span><span class="link-icon__img"></span></a></div>
                                          </div>
                                          <div class="trade-panel__actions"><button class="btn btn-hover --round-all btn-medium" style="" data-toggler-id="modalCollectDesktop" data-toggler-desktop-id="modalCollectDesktop"><span class="btn-title --up text-grad grad-yellow-down"><svg class="icon-svg icon-svg_hand-coins btn-title-icon">
                                                          <use xlink:href="#hand-coins"></use>
                                                      </svg> <span>Collect</span></span></button></div>
                                      </div>
                                  </div>
                                  <div class="wrapper px-10">
                                      <div class="divider-title --mb-big">Crypto Wallets</div>
                                      <div class="trade-panel">
                                          <div class="trade-panel__row --panel">
                                              <div class="trade-panel__left">
                                                  <div class="trade-panel-title">AGT Wallet</div>
                                                  <div class="trade-panel__description color-light">Save exceeding Gold Points by exchanging them to AGT.</div>
                                              </div>
                                              <div class="trade-panel__right"><a class="link-icon"><span class="link-icon__text color-light">799 AGT </span><span class="link-icon__img"><svg class="icon-svg icon-svg_chevron-right">
                                                              <use xlink:href="#chevron-right"></use>
                                                          </svg></span></a></div>
                                          </div>
                                          <div class="trade-panel__actions"><button class="btn btn-hover --round-br --success btn-medium" style=""><span class="btn-title --up text-grad grad-yellow-down"><svg class="icon-svg icon-svg_receive btn-title-icon">
                                                          <use xlink:href="#receive"></use>
                                                      </svg> <span>Receive</span></span></button> <button class="btn btn-hover --round-r --success btn-medium" style=""><span class="btn-title --up text-grad grad-yellow-down"><svg class="icon-svg icon-svg_transfer btn-title-icon">
                                                          <use xlink:href="#transfer"></use>
                                                      </svg> <span>Transfer</span></span></button></div>
                                      </div>
                                      <div class="trade-panel">
                                          <div class="trade-panel__row --panel">
                                              <div class="trade-panel__left">
                                                  <div class="trade-panel-title">BNB Wallet</div>
                                                  <div class="trade-panel__description color-light">The balance of your BNB wallet. Top up from any of your wallets or exchanges.</div>
                                              </div>
                                              <div class="trade-panel__right"><a class="link-icon"><span class="link-icon__text color-light">599 BNB </span><span class="link-icon__img"><svg class="icon-svg icon-svg_chevron-right">
                                                              <use xlink:href="#chevron-right"></use>
                                                          </svg></span></a></div>
                                          </div>
                                          <div class="trade-panel__actions"><button class="btn btn-hover --round-br --success btn-medium" style=""><span class="btn-title --up text-grad grad-yellow-down"><svg class="icon-svg icon-svg_receive btn-title-icon">
                                                          <use xlink:href="#receive"></use>
                                                      </svg> <span>Receive</span></span></button> <button class="btn btn-hover --round-r --success btn-medium" style=""><span class="btn-title --up text-grad grad-yellow-down"><svg class="icon-svg icon-svg_transfer btn-title-icon">
                                                          <use xlink:href="#transfer"></use>
                                                      </svg> <span>Transfer</span></span></button></div>
                                      </div>
                                  </div>
                              </div>
                          </div>
                      </div>
                      <div class="menu-full-body__right custom-scroll">
                          <div class="menu-container">
                              <div class="account-history-content">
                                  <div class="wrapper">
                                      <div class="divider-title --mb-big">Pending Transactions</div>
                                      <div class="trade-panel">
                                          <div class="trade-panel__row">
                                              <div class="trade-panel__left">
                                                  <div class="trade-panel-title"><span class="trade-panel-title__icon"><svg class="icon-svg icon-svg_incoming">
                                                              <use xlink:href="#incoming"></use>
                                                          </svg> </span>Incoming transaction</div>
                                              </div>
                                              <div class="trade-panel__right"><a class="link-icon"><span class="link-icon__text">29 BNB </span><span class="link-icon__img"><svg class="icon-svg icon-svg_s icon-svg_s-link-out">
                                                              <use xlink:href="#s-link-out"></use>
                                                          </svg></span></a></div>
                                          </div>
                                          <div class="trade-panel__row">
                                              <div class="trade-panel__left">
                                                  <div class="trade-panel-title"><span class="trade-panel-title__icon"><svg class="icon-svg icon-svg_outgoing">
                                                              <use xlink:href="#outgoing"></use>
                                                          </svg> </span>Outgoing transaction</div>
                                              </div>
                                              <div class="trade-panel__right"><a class="link-icon"><span class="link-icon__text">19 AGT </span><span class="link-icon__img"><svg class="icon-svg icon-svg_s icon-svg_s-link-out">
                                                              <use xlink:href="#s-link-out"></use>
                                                          </svg></span></a></div>
                                          </div>
                                      </div>
                                  </div>
                                  <div class="wrapper">
                                      <div class="divider-title --mb-big">History</div>
                                      <div class="trade-panel">
                                          <div class="trade-panel__row">
                                              <div class="trade-panel__left">
                                                  <div class="trade-panel-title"><span class="trade-panel-title__icon"><svg class="icon-svg icon-svg_incoming">
                                                              <use xlink:href="#incoming"></use>
                                                          </svg> </span>Incoming transaction</div>
                                              </div>
                                              <div class="trade-panel__right"><a class="link-icon"><span class="link-icon__text">29 BNB </span><span class="link-icon__img"><svg class="icon-svg icon-svg_s icon-svg_s-link-out">
                                                              <use xlink:href="#s-link-out"></use>
                                                          </svg></span></a></div>
                                          </div>
                                          <div class="trade-panel__row">
                                              <div class="trade-panel__left">
                                                  <div class="trade-panel-title"><span class="trade-panel-title__icon"><svg class="icon-svg icon-svg_outgoing">
                                                              <use xlink:href="#outgoing"></use>
                                                          </svg> </span>Outgoing transaction</div>
                                              </div>
                                              <div class="trade-panel__right"><a class="link-icon"><span class="link-icon__text">19 AGT </span><span class="link-icon__img"><svg class="icon-svg icon-svg_s icon-svg_s-link-out">
                                                              <use xlink:href="#s-link-out"></use>
                                                          </svg></span></a></div>
                                          </div>
                                          <div class="trade-panel__row">
                                              <div class="trade-panel__left">
                                                  <div class="trade-panel-title"><span class="trade-panel-title__icon"><svg class="icon-svg icon-svg_s icon-svg_s-refresh">
                                                              <use xlink:href="#s-refresh"></use>
                                                          </svg> </span>Trade</div>
                                              </div>
                                              <div class="trade-panel__right"><a class="link-icon">
                                                      <div class="link-icon__text">20 AGT → <span class="color-acsent">2000 GP</span></div><span class="link-icon__img"><svg class="icon-svg icon-svg_s icon-svg_s-link-out">
                                                              <use xlink:href="#s-link-out"></use>
                                                          </svg></span>
                                                  </a></div>
                                          </div>
                                      </div>
                                  </div>
                              </div>
                          </div>
                      </div>
                  </div>
              </div>
          </div>
      </div>
      <div class="modal-footer mt-a desktop-hidden">
          <div class="container">
              <div class="modal-actions"><button class="btn btn-hover --decor" style=""><span class="btn-decor"></span> <span class="btn-title --up text-grad grad-yellow-down"><svg class="icon-svg icon-svg_trade btn-title-icon">
                              <use xlink:href="#trade"></use>
                          </svg> <span>Trade</span></span></button> <button class="btn btn-hover --decor" style=""><span class="btn-decor"></span> <span class="btn-title --up text-grad grad-yellow-down"><svg class="icon-svg icon-svg_market btn-title-icon">
                              <use xlink:href="#market"></use>
                          </svg> <span>Market</span></span></button></div>
          </div>
      </div>
  </div>
</div><svg style="height: 0;">
  <defs>
      <linearGradient id="divider-light" x1="0" y1="4.00003" x2="160" y2="4.00001" gradientUnits="userSpaceOnUse">
          <stop stop-color="#FB9340" stop-opacity="0" />
          <stop offset="0.500284" stop-color="#FB9340" />
          <stop offset="1" stop-color="#FB9340" stop-opacity="0" />
      </linearGradient>
      <linearGradient id="divider-dark" x1="0" y1="4.00003" x2="160" y2="4.00001" gradientUnits="userSpaceOnUse">
          <stop />
          <stop offset="0.500284" stop-color="#EC6219" />
          <stop offset="1" />
      </linearGradient>
  </defs>
</svg> <object id="sprite-svg" data="/assets/images/sprite.svg" type="image/svg+xml"></object>
