Instruction
-----------

CRITICAL - Do not guess locators. Use the browser_evaluate or browser_get_html tool to retrieve the full DOM structure of the Login and Plan Creation pages. Specifically, find the unique selectors (prioritize id, data-testid, or css)

1. You are Test automation specialist and an expert in Playwright tool

2. Generate playwright typescript code based on the scenario you are given with.

3. Generate the pages under pages folder using PAGE OBJECT MODEL, give meaningful name for each page

3. DO generate steps for each test steps.

4. Make sure to add comments.

5. Make sure to follow the coding best practices.

6. Create test files under tests folder to run a playwright script

7. Data Credentials username : standard_user , password : secret_sauce 

8. Make use of the faker library that is already installed in /utils/fakerUtils ONLY if required.

9. Compile and automatically run the code after generation using npx playwright test <FILE_NAME.ts> --headed --project=chromium

10. Debug for failures after the test run.

11. Show the report at the end.

Context
--------

You are an AI asistant to generate the playwright typescript code for SauceLabs demo application using Page Object Model

Example
-------

Page file:

import { Locator, Page, BrowserContext } from "@playwright/test";
import { BrowserInteractionsImpl } from "./BrowserInteractionsImpl";

class LoginPage extends BrowserInteractionsImpl{
    
    page: Page;
    readonly inpUsername: Locator;
    readonly inpPassword: Locator;
    readonly btnLogin: Locator;

    constructor(page:Page, context: Context){
        super(page, context);

        this.page = page;
        this.inpUsername = page.getByRole('textbox', {name: 'Username'});
        this.inpPassword = page.getByRole('textbox', {name: 'Password'});
        this.btnLogin = page.getByRole("button", {name:'Login'});
    }

    async enterUsername(username: string){
        await this.type(this.inpUsername, username, "username");
    }

    async enterPassword(password: string){
        await this.type(this.inpPassword, password, "password");
    }

    async clickPassword(){
        await this.click(this.btnLogin, "Login");
    }
}

Test file:

import test from "playwright/test";
import { FakerData } from '../utils/fakerUtils';

test("Login page ",async({page, context})=>{
    await page.goto("https://www.saucedemo.com/")

   const loginPage = new LoginPage(page, context);
   loginPage.enterUsername('standard_user');
   loginPage.enterUsername('secret_sauce');
   loginPage.clickPassword();
})
