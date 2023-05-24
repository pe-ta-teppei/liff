async function getUserAnswers() {

    // 事前にliff.init()が完了していると仮定します。



    // ユーザーが選択するオプション

    const options = {

        'experience': ['はじめて', 'やったことがある'],

        'purpose': ['自己処理の手間を減らしたい', '肌をきれいにしたい', 'ムダ毛の悩みを解消したい'],

        'priority': ['効果', '価格', '痛み', 'アフターケア'],

        'area': ['全身脱毛', '背中・うなじ', 'VIO', 'その他'],

        'budget': ['〜10,000円', '〜20,000円', '〜30,000円', '〜50,000円', 'プランによる'],

        'region': ['北海道', '青森県', '岩手県', '宮城県', '秋田県', '山形県', '福島県', '茨城県', '栃木県', '群馬県', '埼玉県', '千葉県', '東京都', '神奈川県', '新潟県', '富山県', '石川県', '福井県', '山梨県', '長野県', '岐阜県', '静岡県', '愛知県', '三重県', '滋賀県', '京都府', '大阪府', '兵庫県', '奈良県', '和歌山県', '鳥取県', '島根県', '岡山県', '広島県', '山口県', '徳島県', '香川県', '愛媛県', '高知県', '福岡県', '佐賀県', '長崎県', '熊本県', '大分県', '宮崎県', '鹿児島県', '沖縄県']

    };



    // 選択された回答を保持するオブジェクト

    const answers = {};



    // 各質問についてユーザーの選択を取得

    for (const [question, choices] of Object.entries(options)) {

        const userChoice = await getUserChoice(question, choices);

        answers[question] = userChoice;

    }



    // 選択された回答をトークルームに投稿

    if (liff.isLoggedIn()) {

        liff.sendMessages([

            {

                'type': 'text',

                'text': JSON.stringify(answers, null, 2)

            }

        ]);

    } else {

        // ユーザーがログインしていなければログインを要求

        liff.login();

    }

}



// ユーザーに質問を提示し、選択肢から選択させる関数

// この実装は、あなたのフロントエンドフレームワークに依存します

async function getUserChoice(question, choices) {

    // ...

}
