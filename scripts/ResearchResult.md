---
marp: true
headingDivider: 3
---


`I will investigate and learn what kind of structure and prompts are being used.`

- 2023/4/13(Thu) n-ao

## Script全体構成

### scripts以外
```sh
├── CONTRIBUTING.md
├── Dockerfile
├── LICENSE
├── README.md
├── azure.yaml.template
├── main.py
├── outputs
│   ├── guest_post_email.txt
│   ├── how_to_save_money_on_energy_bills.txt
│   ├── logs
│   │   ├── message-log-1.txt
│   │   ├── message-log-2.txt
│   │   ├── message-log-3.txt
│   │   └── message-log-4.txt
│   ├── post1_output.txt
│   └── post2_output.txt
├── requirements.txt
```

## scripts
```sh
├── scripts
│   ├── __init__.py
│   ├── agent_manager.py
│   ├── ai_config.py
│   ├── ai_functions.py
│   ├── browse.py
│   ├── call_ai_function.py
│   ├── chat.py
│   ├── commands.py
│   ├── config.py
│   ├── data
│   │   └── prompt.txt
│   ├── data.py
│   ├── execute_code.py
│   ├── file_operations.py
│   ├── image_gen.py
│   ├── json_parser.py
│   ├── json_utils.py
│   ├── llm_utils.py
│   ├── logger.py
│   ├── main.py
│   ├── memory
│   │   ├── __init__.py
│   │   ├── base.py
│   │   ├── local.py
│   │   ├── pinecone.py
│   │   └── redismem.py
│   ├── speak.py
│   ├── spinner.py
│   ├── token_counter.py
│   └── utils.py
```

### tests
```sh
├── tests
│   ├── __init__.py
│   ├── context.py
│   ├── integration
│   │   └── memory_tests.py
│   ├── local_cache_test.py
│   ├── test_config.py
│   ├── test_json_parser.py
│   └── unit
│       ├── json_tests.py
│       ├── test_browse_scrape_links.py
│       └── test_browse_scrape_text.py
└── tests.py
```


## パフォーマンス評価のプロンプト
- [PERFORMANCE EVALUATION:](https://github.com/n-ao/Auto-GPT/blob/c8b8673286f643c689a7009d53f1737df32742f6/scripts/data/prompt.txt#L37-L42)

```txt
PERFORMANCE EVALUATION:

1. Continuously review and analyze your actions to ensure you are performing to the best of your abilities.
2. Constructively self-criticize your big-picture behavior constantly.
3. Reflect on past decisions and strategies to refine your approach.
4. Every command has a cost, so be smart and efficient. Aim to complete tasks in the least number of steps.
```

## json出力指示
- [ソース](https://github.com/n-ao/Auto-GPT/blob/c8b8673286f643c689a7009d53f1737df32742f6/scripts/data/prompt.txt#L43-L62)

```json
You should only respond in JSON format as described below

RESPONSE FORMAT:
{
    "thoughts":
    {
        "text": "thought",
        "reasoning": "reasoning",
        "plan": "- short bulleted\n- list that conveys\n- long-term plan",
        "criticism": "constructive self-criticism",
        "speak": "thoughts summary to say to user"
    },
    "command": {
        "name": "command name",
        "args":{
            "arg name": "value"
        }
    }
}
```