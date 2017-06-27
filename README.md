# jquery.validate.supportBank

数据更新时间：2016年5月7日

## How to use
···js
$(form).eq(0).validate({
  submitHandler: function(form) {
    
  },
  onkeyup: false,
  errorPlacement: function(error, element) {
    console.log(error);
  },
  highlight: function(element, errorClass, validClass) {
    var errorMsg = $(element).attr('data-tips');
    console.log(errorMsg);
  },
  success: function(label,element) {
    var success = $(element).attr('data-tips') || '';
    console.log(success);
  },
  rules: {
    bankcard: {
      required:true,
      support_bank: {
        type:1,                                                   //支持的银行卡类型，1:借记卡, 2:借贷卡, 3:准借贷卡, 4:预付款卡
        support: [                                                //支持的银行列表，如中国建设银行，可模糊填写为建设银行。其他银行名称请参考插件里的银行列表
          '建设银行',
          '兴业银行',
          '中信银行',
          '民生银行',
          '光大银行',
          '平安银行',
          '广发银行',
          '招商银行',
          '工商银行',
          '农业银行',
          '中国银行'
        ],
        notSupport: {
          name: ['北京银行','厦门国际银行','华夏银行'],           //不知此的银行卡列表
          prefix: [95595,95596,95597,95598]                       //不支持的银行卡前缀
        },
        options: {
          cardTypes: [                                            //银行卡类型
            '借记卡(储蓄卡)',
            '借贷卡(信用卡)',
            '准借贷卡(信用卡)',
            '预付款卡(信用卡)'
          ],
          errorLength: '您输入的银行卡号(位数)不正确。',          //银行卡位数不匹配错误信息
          errorType: '不支持{0}。',                               //不支持的银行卡类型错误信息
          msgIncomplete: '此卡可以进行绑定，但不能用于快捷充值。' //不完全支持的类型（不在支持列表里，也不在不支持列表里的）
        }
      }
    }
  },
  messages: {
    bankcard: {
      required: '请输入银行卡号。',
      support_bank: '暂不支持此卡或输入有误。'
    }
  }
});
···