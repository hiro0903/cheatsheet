CSS Hack
========
|  ie11 and below |  color: green\0; |
|  ie10 and below |  color: red\9;   |
|  ie7  and below | *color: yellow;  |
|  ie6            | _color: orange;  |


IE 條件
=======
|  `<!--[if IE]>內容<![endif]-->`                  | 內容只有 IE 會顯現。                           |
|  `<!--[if IE 6]>內容<![endif]-->`                | 內容只有 IE6 會顯現                            |
|  `<!--[if lt IE 7]>內容<![endif]-->              | 內容只在比 IE7 更舊的版本會顯現                |
|  `<!--[if gte IE 8]>內容<![endif]-->             | 內容只有 IE8 及其較新版本會顯現                |
|  `<!--[if !IE]>-->內容<!--<![endif]-->           | 內容除 IE 以外都會顯現                         |
|  `<!--[if !(IE 6)]>內容<![endif]-->              | 內容除 IE6 以外的 IE 都會顯現                  |
|  `<!--[if (gte IE 6)&(lt IE 8)]>內容<![endif]--> | 內容只從 IE6 以後及 IE8 之前版本會顯現         |
|  `<!--[if (IE 7)|(IE 8)]>內容<![endif]-->        | 內容只有 IE7 及 IE8 會顯現                     |
|  `<!--[if gte IE 7]><!-->內容<!--<![endif]-->`   | 內容在 IE7 及其較新版本，以及 IE 以外都會顯現  |

要在template中使用, 需要在`[if]`, `[endif]` 前面加上反斜線: `\[if]`, `\[endif]`
