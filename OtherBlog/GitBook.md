# GitBook教程

## 学习GitBook推荐
> [GitBook推荐博客](http://gitbook.zhangjikai.com/index.html)

> [GitBook用法](https://www.jianshu.com/p/bd8cc5c7b7b5)

### 配置文件

	book.json
	{
	  "title": "",
	  "language": "zh-hans",
	  "plugins": [
	    "-sharing",
	    "copy-code-button",
	    "anchor-navigation-ex",
	    "-lunr",
	    "-search",
	    "search-plus",
	    "expandable-chapters-small",
	    "splitter"
	  ],
	  "pluginsConfig": {
	    "theme-default": {
	      "showLevel": true
	    },
	    "anchor-navigation-ex": {
	      "showLevel": true,
	      "associatedWithSummary": false,
	      "multipleH1": false,
	      "float": {
	        "showLevelIcon": true,
	        "level1Icon": "fa fa-hand-o-right",
	        "level2Icon": "fa fa-hand-o-right",
	        "level3Icon": "fa fa-hand-o-right"
	      }
	    }
	  }
	}

 	package.json
	{
	  "dependencies": {
	    "gitbook": ">=3.0.0",
	    "gitbook-plugin-anchor-navigation-ex": "^1.0.11",
	    "gitbook-plugin-copy-code-button": "^0.0.2",
	    "gitbook-plugin-expandable-chapters-small": "^0.1.7",
	    "gitbook-plugin-search-plus": "^1.0.4-alpha-3",
	    "gitbook-plugin-search-pro": "^2.0.2",
	    "gitbook-plugin-splitter": "^0.0.8",
	    "gitbook-plugin-theme-faq": "^1.2.1"
	  }
	}
