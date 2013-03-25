ie-placeholder
==============

input/textarea[placeholder] compatible ie6-ie9

主要用来解决IE6-IE9不支持placeholder属性，


```css
/*=placeholder color= S*/
input{color:black;}
input::-webkit-input-placeholder,
textarea::-webkit-input-placeholder{color:#69C;}
.ie-placeholder{color:#69C;}
input::-moz-placeholder,
textarea::-moz-placeholder{color:#69C;opacity:1;}
input:-ms-input-placeholder,
textarea:-ms-input-placeholder{color:#69C;}
/*=placeholder color= E*/
```
```html
<input type="text" placeholder='ie-placeholder' >
```
```javascript
$(function(){
  fnPlaceholder()	
})
var fnPlaceholder=function(){
	if(!('placeholder' in document.createElement('input'))){/* nonsupport placeholder*/
		$("input[placeholder],textarea[placeholder]").closest('form').has(':reset').bind('reset',function(){/*click reset*/
			setTimeout(function(){
				$("input[placeholder],textarea[placeholder]").each(function(){
	 				$(this).val($(this).attr('placeholder')).addClass('ie-placeholder');
	 			})	 			
			},0)

		})
		$("input[placeholder],textarea[placeholder]").each(function(){
			$(this).val($(this).attr('placeholder')).addClass('ie-placeholder');
		}).bind('focus',function(){
			if($(this).val()==$(this).attr('placeholder')){
				$(this).val("").removeClass('ie-placeholder')
			}
		}).bind('blur',function(){
			if($(this).val().length==0){
			$(this).val($(this).attr('placeholder')).addClass('ie-placeholder')
			}
		})
	}
}
```
