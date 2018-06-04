# Feedreader-test
# Overview
This the Feedreader-test submission for FEND course. Ill walk you through on how to implement the necessary tests for your feedreader to make sure it works as intended.

# Download the project
Download the proect, unpack it anywhere in your harddrive. Then, navigate the jasmine spec folder and open the "feedreader.js"

# Testing names and URLs

        /* Write a test that loops through each feed
         * in the allFeeds object and ensures it has a URL defined
         * and that the URL is not empty.
         */
		 
		it('url is defined', function() {
			allFeeds.forEach(function(feeds) {
				expect(feeds.url).toBeDefined();
				expect(feeds.url.length).toBeGreaterThan(0);
			});
		});
		

        /* test that loops through each feed
         * in the allFeeds object and ensures it has a name defined
         * and that the name is not empty.
         */
		 
		it('has a valid name', function() {
			allFeeds.forEach(function(feeds) {
				expect(feeds.name).toBeDefined(); //is defined 
				expect(feeds.name.length).toBeGreaterThan(0); // Is not empty
			});
		});
		
	});
  
# Checking menu functionality

    describe('The menu', function() {
        /* This tests that the menu element is always hidden by default */
		
        it('menu is hidden by default', function() {
            expect($('body').hasClass('menu-hidden')).toBe(true); //Check that Body element has class menu-hidden by default
        });

        /* Tests that the menu is shown when the menu icon is clicked */
        it('menu is visible when menu icon is clicked', function() {

            $('.menu-icon-link').click();
				expect($('body').hasClass('menu-hidden')).toBe(false); //is menu-hidden set to false when clicked

            $('.menu-icon-link').click();
				expect($('body').hasClass('menu-hidden')).toBe(true); // Vice versa
        });
    });
    
# Initial entries test suite, checking feed length
    /* Test suite named "Initial Entries" */

	describe('Initial Entries', function () {
		
		let feed_length;
		
		beforeEach(function(done) {
			loadFeed(0, function() {
				feed_length = $('.feed .entry').length; // Get div with class "feed", and all its children under "entry" class and count their length
				done();
			});
		});
		
		it('Is not empty', function(done) {
			expect(feed_length).toBeGreaterThan(0);
			done();
		});
	});

# New feed selection
describe('New Feed Selection', function() {

    let feedA,
        feedB;

    beforeEach(function(done) {
        loadFeed(0, function() {
            feedA = document.querySelector('.feed').innerHTML;
        });

        loadFeed(1, function() {
            feedB = document.querySelector('.feed').innerHTML;
            done();
        });
    });

    it('this loads new feeds', function(done) {
        expect(feedB !== feedA).toBe(true);
        done();
    });
});
}());
